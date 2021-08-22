---
layout: tutorial_v2
title: Extending Leaflet, New Layers
---

<br>

本教程假定你已经阅读了 [Leaflet类的继承原理](./extending-1-classes.html)。

在 Leaflet 中，“layer” 是指当地图移动时移动的任何东西。在了解如何从头开始创建它们之前，先解释一下如何进行简单的扩展。

## "扩展方法"

一些 Leaflet 类具有所谓的 “扩展方法”：为子类编写代码的入口点。

其中之一是 `L.TileLayer.getTileUrl()`。每当一个新的瓦片需要知道加载哪张图片时，`L.TileLayer` 就会在内部调用这个方法。通过制作 `L.TileLayer` 的子类并重写其 `getTileUrl()` 函数，我们可以创建自定义行为。

让我们用一个自定义 `L.TileLayer` 来说明，它将显示来自[PlaceKitten]()的随机猫咪图像：

    L.TileLayer.Kitten = L.TileLayer.extend({
        getTileUrl: function(coords) {
            var i = Math.ceil( Math.random() * 4 );
            return "https://placekitten.com/256/256?image=" + i;
        },
        getAttribution: function() {
            return "<a href='https://placekitten.com/attribution.html'>PlaceKitten</a>"
        }
    });

    L.tileLayer.kitten = function() {
        return new L.TileLayer.Kitten();
    }

    L.tileLayer.kitten().addTo(map);

{% include frame.html url="kittenlayer.html" %}

通常，`getTileUrl()` 接收瓦片（tile）坐标（如 `coords.x`、`coords.y`和 `coords.z`），并从中生成一个瓦片（tile）URL。在我们的例子中，我们忽略了这些，只是用一个随机数来获得不同的小猫。

### 拆分插件代码

在前面的示例中，`L.TileLayer.Kitten` 定义在与使用相同的位置。对于插件，最好将插件代码拆分成自己的文件，使用时引入该文件。

对于 KittenLayer，您应该创建一个文件，例如 `L.KittenLayer.js`：

    L.TileLayer.Kitten = L.TileLayer.extend({
        getTileUrl: function(coords) {
            var i = Math.ceil( Math.random() * 4 );
            return "https://placekitten.com/256/256?image=" + i;
        },
        getAttribution: function() {
            return "<a href='https://placekitten.com/attribution.html'>PlaceKitten</a>"
        }
    });

然后，在显示地图时引入该文件：

	<html>
	…
	<script src='leaflet.js'>
	<script src='L.KittenLayer.js'>
	<script>
		var map = L.map('map-div-id');
		L.tileLayer.kitten().addTo(map);
	</script>
	…


### `L.GridLayer` 和 DOM 元素

另一种扩展方法是 `L.GridLayer.createTile()`。`L.TileLayer` 会把它当成一个图片的网格（如`<img>`元素）来处理，`L.GridLayer` 则允许创建任何种类的[HTML元素]的网格(https://developer.mozilla.org/en-US/docs/Web/HTML/Element)。

`L.GridLayer` 允许创建 `<img>` 的网格，但 [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div)、[`<canvas>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/canvas) 或 [`<picture>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture)（或任何东西）的网格也是可以的。`createTile()` 只需要返回  [`HTMLElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement)  给定瓦片（tile）坐标的实例。了解如何操作 [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction) 中的元素在这里很重要：Leaflet 需要实例 `HTMLElement`，因此使用 jQuery 等库创建的元素将有问题。

自定义的一个示例是在 .xml 文件 `GridLayer` 中显示瓦片（tile）坐标 <div>。这在调试 Leaflet 的内部结构以及了解 tile 坐标如何工作时特别有用：

	L.GridLayer.DebugCoords = L.GridLayer.extend({
		createTile: function (coords) {
			var tile = document.createElement('div');
			tile.innerHTML = [coords.x, coords.y, coords.z].join(', ');
			tile.style.outline = '1px solid red';
			return tile;
		}
	});

	L.gridLayer.debugCoords = function(opts) {
		return new L.GridLayer.DebugCoords(opts);
	};

	map.addLayer( L.gridLayer.debugCoords() );


如果元素必须做一些异步初始化，那么就使用第二个函数参数 `done`，并在瓦片（tile）准备好时（例如，当图像已被完全加载）或出现错误时回调它。在这里，我们将人为地延迟瓷砖：

	createTile: function (coords, done) {
		var tile = document.createElement('div');
		tile.innerHTML = [coords.x, coords.y, coords.z].join(', ');
		tile.style.outline = '1px solid red';

		setTimeout(function () {
			done(null, tile);	// Syntax is 'done(error, tile)'
		}, 500 + Math.random() * 1500);

		return tile;
	}

{% include frame.html url="gridcoords.html" %}

通过这些自定义的 `GridLayer`，一个插件可以完全控制构成网格的HTML元素。一些插件已经通过这种方式使用 `<canvas>` 来做高级渲染。

一个非常基础的 `<canvas>` `GridLayer` 类似这样：

	L.GridLayer.CanvasCircles = L.GridLayer.extend({
		createTile: function (coords) {
			var tile = document.createElement('canvas');

			var tileSize = this.getTileSize();
			tile.setAttribute('width', tileSize.x);
			tile.setAttribute('height', tileSize.y);

			var ctx = tile.getContext('2d');

			// Draw whatever is needed in the canvas context
			// For example, circles which get bigger as we zoom in
			ctx.beginPath();
			ctx.arc(tileSize.x/2, tileSize.x/2, 4 + coords.z*4, 0, 2*Math.PI, false);
			ctx.fill();

			return tile;
		}
	});

{% include frame.html url="canvascircles.html" %}


## The pixel origin 像素原点

创建自定义的 "L.Layer "是可能的，但需要对Leaflet如何定位HTML元素有更深的了解。精简版是：

* 该 L.Map 容器具有"地图窗格（pane）"，这是<div>
* `L.Layer` 是地图窗格内的HTML元素
* 地图将所有 `LatLng` 转换为地图CRS中的坐标，再从CRS中转换为绝对的 "像素坐标"（CRS的原点与像素坐标的原点相同）
* 当 `L.Map` 准备好时（有一个中心 `LatLng` 和一个缩放级别），左上角的绝对像素坐标成为 "像素原点"
* 每个 `L.Layer` 都根据像素原点和该层 `LatLng` 的绝对像素坐标从其地图窗格中偏移
* 在 `L.Map` 上的每个 `zoomend` 或 `viewreset` 事件后，像素原点被重置，每个 `L.Layer` 必须重新计算其位置（如果需要的话）
* 在平移地图时，像素原点不会被重置；相反，整个窗格会被重新定位

这可能有点难以理解，因此请参考以下用来解释的地图：

{% include frame.html url="pixelorigin.html" %}

CRS原点（绿色）保持在同一个`LatLng`。像素原点（红色）总是从左上角开始。当地图被平移时，像素原点会移动（地图窗格会相对于地图的容器重新定位），而当缩放时，像素原点会保持在屏幕的同一位置（地图窗格（pane）不会被重新定位，但图层可能会重新绘制）。缩放时对像素原点的绝对像素坐标会被更新，但平移时不会被更新。请注意每次放大地图时，绝对像素坐标（到绿色括号的距离）是如何翻倍的。

如果要定位任何东西（例如，一个蓝色的`L.Marker'），它的`LatLng'被转换为地图的`L.CRS'内的绝对像素坐标。然后从它的绝对像素坐标中减去像素原点的绝对像素坐标，得到一个相对于像素原点（浅蓝色）的偏移。由于像素原点是所有地图窗格的左上角，这个偏移量可以应用于标记的图标的HTML元素。标记的`iconAnchor'（深蓝色线）是通过负的CSS边距实现的。

在 `L.Map.project()` 和 `L.Map.unproject()` 这些绝对像素坐标的方法进行操作。同样，`L.Map.latLngToLayerPoint()`和`L.Map.layerPointToLatLng()`也是使用相对于像素原点的偏移。

不同的层以不同的方式应用这些计算。`L.Marker` 只需重新定位他们的图标；`L.GridLayer` 计算地图的边界（在绝对像素坐标中），然后计算要请求的瓦片坐标列表；矢量图层（折线、多边形、圆形标记等）将每个图层转换 `LatLng` 为像素并使用 SVG 或 `<canvas>`。


### `onAdd` 和 `onRemove`

从本质上讲，所有 `L.Layer` 都是地图窗格中的 HTML 元素，它们的位置和内容由图层代码定义。但是，在实例化图层时无法创建 HTML 元素；相反，这是在将图层添加到地图时完成的 - 图层 document 直到那时才知道地图（甚至不知道）。

换句话说：地图调用图层的 `onAdd()` 方法，然后图层创建其HTML元素（通常称为'容器'元素）并将其添加到地图窗格中。反之，当图层从地图上删除时，它的 `onRemove()` 方法会被调用。当添加到地图上时，图层必须更新其内容，并在地图视图更新时重新定位它们。图层骨架如下所示：

	L.CustomLayer = L.Layer.extend({
		onAdd: function(map) {
			var pane = map.getPane(this.options.pane);
			this._container = L.DomUtil.create(…);

			pane.appendChild(this._container);

			// Calculate initial position of container with `L.Map.latLngToLayerPoint()`, `getPixelOrigin()` and/or `getPixelBounds()`

			L.DomUtil.setPosition(this._container, point);

			// Add and position children elements if needed

			map.on('zoomend viewreset', this._update, this);
		},

		onRemove: function(map) {
			L.DomUtil.remove(this._container);
			map.off('zoomend viewreset', this._update, this);
		},

		_update: function() {
			// Recalculate position of container

			L.DomUtil.setPosition(this._container, point);        

			// Add/remove/reposition children elements if needed
		}
	});

如何准确定位图层的 HTML 元素取决于图层的具体情况，但本介绍应该可以帮助您阅读 Leaflet 的图层代码，并创建新图层。

### 使用父级的 `onAdd`

有些用例不需要重新创建整个 "onAdd "代码，而是可以重复使用父类的代码，然后可以在初始化之前或之后（根据需要）添加一些具体内容。

举个例子，我们可以有一个 `L.Polyline` 始终为红色的子类（忽略选项），例如：

	L.Polyline.Red = L.Polyline.extend({
		onAdd: function(map) {
			this.options.color = 'red';
			L.Polyline.prototype.onAdd.call(this, map);
		}
	});
