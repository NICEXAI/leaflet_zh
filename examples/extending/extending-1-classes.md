---
layout: tutorial_v2
title: Extending Leaflet, Class Theory
---

## 扩展 Leaflet

Leaflet 有数以百计的插件，这些插件扩展了 Leaflet 的功能：有时是以一种通用的方式，有时是以一种非常具体的使用方式。

有这么多插件的部分原因是 Leaflet 易于扩展。本教程将介绍最常用的方法。

请注意，本教程假设您已经很好地掌握了：

* [JavaScript](https://developer.mozilla.org/en-US/Learn/JavaScript)
* [DOM 处理](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction)
* [面向对象编程](https://en.wikipedia.org/wiki/Object-oriented_programming) （理解类、实例、继承、方法和属性等概念）


## Leaflet 架构

让我们看看 Leaflet 1.0.0 的简化 UML 类图。有 60 多个 JavaScript 类，所以图有点大。幸运的是，我们可以用 `L.ImageOverlay` 做一个可缩放的图片：

{% include frame.html url="class-diagram.html" %}


从技术角度来看，Leaflet 可以通过不同的方式进行扩展：

* 最常用的方式是: 使用 `L.Class.extend()` 来创建一个新的 `L.Layer`, `L.Handler` 或者 `L.Control` 的子类
	* 当地图移动/缩放时图层会移动
	* 处理程序不可见并解释浏览器事件
	* 控件是固定的界面元素
* 用 `L.Class.include()` 在一个现有的类中加入更多的功能
	* 添加新方法和选项
	* 改变一些方法
	* 使用 `addInitHook` 来运行额外的构造器代码
* 用 `L.Class.include()` 改变一个现有类的部分内容（替换一个类方法的工作方式）。

本教程涵盖了一些仅在 Leaflet 1.0.0 中可用的类和方法，如果你正在为以前的版本开发一个插件，请谨慎行事。

## `L.Class`

JavaScript 是一种有点奇怪的语言。它并不是一种真正的面向对象的语言，而是一种[面向原型的语言](https://en.wikipedia.org/wiki/Prototype-based_programming)，这使得 JavaScript 在历史上难以使用经典 OOP 意义上的类继承。

Leaflet 通过 `L.Class` 来解决这个问题，它简化了类的继承。

尽管现代 JavaScript 可以使用 ES6 类，但 Leaflet 并不是围绕它们设计的。

### `L.Class.extend()`

要在 Leaflet 中创建任何内容的子类，请使用该 `.extend()` 方法。它接受一个参数：一个带有键值对的普通对象，每个键是属性或方法的名称，每个值是属性的初始值或方法的实现：

    var MyDemoClass = L.Class.extend({
    
        // A property with initial value = 42
        myDemoProperty: 42,   
    
        // A method 
        myDemoMethod: function() { return this.myDemoProperty; }
        
    });

    var myDemoInstance = new MyDemoClass();
    
    // This will output "42" to the development console
    console.log( myDemoInstance.myDemoMethod() );   

在命名类、方法和属性时，请遵循以下约定：
    
* 函数、方法、属性和工厂名称应使用 [`lowerCamelCase`](https://en.wikipedia.org/wiki/CamelCase)
* 类名应使用 [`UpperCamelCase`](https://en.wikipedia.org/wiki/CamelCase)
* 私有属性和方法以下划线（`_`）开头。这并不意味着它们是私有的，只是建议开发者不要直接使用它们

### `L.Class.include()`    

如果已经定义了一个类，则可以重新定义现有的属性/方法，或者可以使用 `.include()` 方法添加新的属性/方法：

    MyDemoClass.include({
    
        // Adding a new property to the class
        _myPrivateProperty: 78,
        
        // Redefining a method
        myDemoMethod: function() { return this._myPrivateProperty; }
    
    });

    var mySecondDemoInstance = new MyDemoClass();
    
    // This will output "78"
    console.log( mySecondDemoInstance.myDemoMethod() );
    
    // However, properties and methods from before still exist
    // This will output "42"
    console.log( mySecondDemoInstance.myDemoProperty );

### `L.Class.initialize()`

在 OOP 中，类有一个构造方法。在 Leaflet 的 `L.Class` 中，构造方法总是被命名为 `initialize` 。

如果您的类有一些特定的 `options`，最好 `L.setOptions()` 在构造函数中初始化它们。此实用程序函数会将提供的选项与类的默认选项合并。


    var MyBoxClass = L.Class.extend({
    
        options: {
            width: 1,
            height: 1
        },
    
        initialize: function(name, options) {
            this.name = name;
            L.setOptions(this, options);
        }
        
    });
    
    var instance = new MyBoxClass('Red', {width: 10});

    console.log(instance.name); // Outputs "Red"
    console.log(instance.options.width); // Outputs "10"
    console.log(instance.options.height); // Outputs "1", the default

Leaflet 以一种特殊的方式处理 `options` 属性：父类的可用选项将被子类继承：

    var MyCubeClass = MyBoxClass.extend({
        options: {
            depth: 1
        }
    });
    
    var instance = new MyCubeClass('Blue');
    
    console.log(instance.options.width); // Outputs "1", parent class default
    console.log(instance.options.height); // Outputs "1", parent class default
    console.log(instance.options.depth); // Outputs "1"


子类运行父类的构造函数，然后再运行自己的构造函数是很常见的。在 Leaflet 中，这是用 `L.Class.addInitHook()` 实现的。这个方法可以用来 "hook" 初始化函数，在类 `initialize()` 之后直接运行，例如：

    MyBoxClass.addInitHook(function(){
        this._area = this.options.width * this.options.length;
    });

这将在 `initialize()` 被调用后运行（调用 `setOptions()`）。这意味着 `this.options` 存在，并且在 init hook 运行时有效。

`addInitHook` 有另一种语法，它使用方法名，并可以填入方法参数：

    MyCubeClass.include({
        _calculateVolume: function(arg1, arg2) {
            this._volume = this.options.width * this.options.length * this.options.depth;
        }
    });
    
    MyCubeClass.addInitHook('_calculateVolume', argValue1, argValue2);
    

### 父类的方法

调用父类的方法是通过进入父类的原型并使用 [`Function.call(...)`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call) 来实现的。例如，在 `L.FeatureGroup` 的代码中可以看到这一点：

    L.FeatureGroup = L.LayerGroup.extend({
    
        addLayer: function (layer) {
            …
            L.LayerGroup.prototype.addLayer.call(this, layer);
        },
        
        removeLayer: function (layer) {
            …
            L.LayerGroup.prototype.removeLayer.call(this, layer);
        },
    
        …
    });

以类似的方式调用父类的构造函数，使用 `ParentClass.prototype.initialize.call(this, ...)` 来代替。
    
    
### Factories 工厂

大多数 Leaflet 类都有一个相应的[工厂函数](https://en.wikipedia.org/wiki/Factory_%28object-oriented_programming%29)。工厂函数的名称与类相同，但它使用 `lowerCamelCase` 而不是 `UpperCamelCase`：
    
    function myBoxClass(name, options) {
        return new MyBoxClass(name, options);
    }
    
    
### 命名规范

在为 Leaflet 插件命名类时，请遵守以下命名规范：

* 永远不要在你的插件中暴露全局变量
* 如果你有一个新的类，直接把它放在 `L` 命名空间（`L.MyPlugin`）
* 如果你继承了一个现有的类，让它成为一个子属性（`L.TileLayer.Banana`）


