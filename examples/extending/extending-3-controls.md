---
layout: tutorial_v2
title: Extending Leaflet, New Handlers and Controls
---

<br>

本教程假定你已经阅读了 [Leaflet 类的继承原理](./extending-1-classes.html)。

在 Leaflet 中，"图层（layer）"是任何能随地图移动的东西。与此相反，"控件（control）"是一个相对于地图容器保持静态的 HTML 元素，而 "处理程序（handler）"是一段改变地图行为的不可见代码。

## 处理程序（handler）

Map handlers 是 Leaflet 1.0 中的一个新概念，它们的功能是处理来自浏览器的 DOM 事件（例如 `click`、`dblclick`  或  `mousewheel`）并改变地图的状态。

处理程序相对简单：它们只需要一个 `addHooks()` 方法（在映射中启用处理程序时运行）和一个 `removeHooks()` 方法（在禁用处理程序时运行）。处理程序的骨架是：

	L.CustomHandler = L.Handler.extend({
		addHooks: function() {
			L.DomEvent.on(document, 'eventname', this._doSomething, this);
		},

		removeHooks: function() {
			L.DomEvent.off(document, 'eventname', this._doSomething, this);
		},

		_doSomething: function(event) { … }
	});

这可以用一个简单的处理程序来说明，当移动设备倾斜时，通过 [`deviceorientation` 事件]（https://developer.mozilla.org/en-US/docs/Web/API/Detecting_device_orientation）来平移地图：

	L.TiltHandler = L.Handler.extend({
		addHooks: function() {
			L.DomEvent.on(window, 'deviceorientation', this._tilt, this);
		},

		removeHooks: function() {
			L.DomEvent.off(window, 'deviceorientation', this._tilt, this);
		},

		_tilt: function(ev) {
			// Treat Gamma angle as horizontal pan (1 degree = 1 pixel) and Beta angle as vertical pan
			this._map.panBy( L.point( ev.gamma, ev.beta ) );
		}
	});

处理程序可以用 `map.addHandler('tilt', L.TiltHandler)` 附加到地图上 —— 这将把 `L.TiltHandler` 的一个实例存储为 `map.tilt`。然而，更常见的是用 `addInitHook`  语法将处理程序附加到所有地图上：

	L.Map.addInitHook('addHandler', 'tilt', L.TiltHandler);

我们的处理程序现在可以通过运行 `map.tilt.enable()` 来启用，并通过 `map.tilt.disable()` 来禁用

此外，如果地图具有与处理程序名称相同的属性，那么如果该选项为 `true`，则该处理程序将默认启用，因此这将默认启用我们的处理程序：

	var map = L.map('mapDiv', { tilt: true });

如果要看这个例子，你需要一个[支持 `deviceorientation` 事件](http://caniuse.com/#search=deviceorientation) 的移动浏览器 - 即使如此，这个事件也是特别不稳定和不明确的，因此你需要注意这一点。

{% include frame.html url="tilt.html" %}

根据事件的类型，地图处理程序可以将事件监听器附加到 `document`、 `window` 或它所连接的 `L.Map` 的容器上。

## 控件（Controls）

您已经知道控件 - 左上角的缩放控件、左下角的缩放、右上角的图层切换器。本质上，`L.Control` 是一个 HTML 元素，位于地图容器中的静态位置。

要制作一个控件，只需继承 `L.Control` 并实现 `onAdd()` 和 `onRemove()`。这些方法的工作方式与 `L.Layer` 对应的方法类似（每当控件被添加到地图或从地图中移除时，它们都会运行），除了 `onAdd()` 必须返回一个代表控件的 `HTMLElement` 实例。将元素添加到地图上是自动完成的，删除也是如此。

自定义控件的最简单示例是水印，它只是一个图像：

	L.Control.Watermark = L.Control.extend({
		onAdd: function(map) {
			var img = L.DomUtil.create('img');

			img.src = '../../docs/images/logo.png';
			img.style.width = '200px';

			return img;
		},

		onRemove: function(map) {
			// Nothing to do here
		}
	});

	L.control.watermark = function(opts) {
		return new L.Control.Watermark(opts);
	}

	L.control.watermark({ position: 'bottomleft' }).addTo(map);

{% include frame.html url="watermark.html" %}

如果您的自定义控件具有可点击按钮等交互元素，请记得在 `onAdd()` 中使用 `L.DomEvent.on()`，在 `onRemove()`中使用 `L.DomEvent.off()`

如果您的自定义控件包含多个 HTML 元素（比如 `L.Control.Zoom`，它有两个按钮），则您必须创建元素的整个层次结构并返回最顶层的容器。

## 发布属于自己的插件

如果到目前为止你已经了解了所有内容，那么你就可以制作一些 Leaflet 插件了！但请务必阅读 [`PLUGIN-GUIDE.md` 文件](https://github.com/Leaflet/Leaflet/blob/master/PLUGIN-GUIDE.md)，因为它包含有关命名和发布插件的一些提示和最佳实践。
