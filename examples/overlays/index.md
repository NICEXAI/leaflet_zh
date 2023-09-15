---
layout: tutorial_v2
title: Overlays
---

## Overlays（覆盖物图层）

有三种overlays在Leaflet API中: 

- [`ImageOverlay`](/reference.html#imageoverlay): 栅格图层，扩展自 [`Layer`](/reference.html#layer)
- [`VideoOverlay`](/reference.html#videooverlay): 栅格图层，扩展自 [`ImageOverlay`](/reference.html#imageoverlay)
- [`SVGOverlay`](/reference.html#svgoverlay): 矢量图层，扩展自 [`ImageOverlay`](/reference.html#imageoverlay)

在本教程中，您将学习如何使用这三种 overlays。

### `ImageOverlay`

`L.ImageOverlay` 用于在地图的特定边界上加载和显示单个图像。 

使用 [`L.ImageOverlay`](/reference.html#imageoverlay) 添加一个图像覆盖物：

```
var imageOverlay = L.imageOverlay(imageUrl, latLngBounds, options);
```

#### 创建一个地图


首先，创建一个Leaflet地图并且通过`L.TileLayer`添加常用底图：
```
var map = L.map('map').setView([37.8, -96], 4);

var osm = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
	maxZoom: 19,
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);
```

让我们创建一个具有多个选项的图像覆盖物：

```
var imageUrl = 'https://maps.lib.utexas.edu/maps/historical/newark_nj_1922.jpg';
var errorOverlayUrl = 'https://cdn-icons-png.flaticon.com/512/110/110686.png';
var altText = 'Image of Newark, N.J. in 1922. Source: The University of Texas at Austin, UT Libraries Map Collection.';
var latLngBounds = L.latLngBounds([[40.799311, -74.118464], [40.68202047785919, -74.33]]);

var imageOverlay = L.imageOverlay(imageUrl, latLngBounds, {
	opacity: 0.8,
	errorOverlayUrl: errorOverlayUrl,
	alt: altText,
	interactive: true
}).addTo(map);
```

如果您想查看 ImageOverlay 覆盖物的区域，可以将具有相同 `L.LatLngBounds` 的 [`L.Rectangle`](reference.html#rectangle)添加到地图中：

```
L.rectangle(latLngBounds).addTo(map);
map.fitBounds(latLngBounds);
```

- `opacity` 定义图像覆盖物的不透明度， 默认是 `1.0`。减小该值可以使图像覆盖图透明，从而暴露出下面的图层。  
	
- `errorOverlayUrl` 要显示的覆盖图像的URL，以代替加载失败的覆盖物。

- `alt` 设置HTML属性 [`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-alt) 提供替代图像的描述。 替代文本同样也是屏幕阅读器用户的必要信息。它可以在网络连接不良的情况下为人们带来好处。此外，它还可以提高网站的SEO。

- `interactive` 默认是 `false`。如果改为 `true`, 覆盖物图层将会响应鼠标点击或悬浮事件。

您可以找到 `L.ImageOverlay` 的其他参数在 [documentation](/reference.html#imageoverlay).

{% include frame.html url="example-image.html" %}

### `VideoOverlay`

在 [`<video>` HTML element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) 出现之前，视频在网页构建中是一项艰难的任务。

现在，我们可以使用以下HTML代码：

```
<video width="500" controls>
	<source src="https://www.mapbox.com/bites/00188/patricia_nasa.webm" type="video/webm">
	<source src="https://www.mapbox.com/bites/00188/patricia_nasa.mp4" type="video/mp4">
</video>
```

来显示此视频：

<video width="500" controls>
<source src="https://www.mapbox.com/bites/00188/patricia_nasa.webm" type="video/webm">
<source src="https://www.mapbox.com/bites/00188/patricia_nasa.mp4" type="video/mp4">
</video>

如果视频可以这样展示在网页上，那么 Leaflet 也可以把它这样用在地图上。但重要的是，视频的准备方式应适合地图：视频应具有“北上”方向，其比例适合地图。如果没有，它将看起来不合适。

#### 创建一个地图

首先，创建一个Leaflet地图并且通过`L.TileLayer`添加常用底图：

```
var map = L.map('map').setView([37.8, -96], 4);

var osm = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
	maxZoom: 19,
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);
```

#### 添加视频覆盖物

添加视频覆盖的工作与添加图像覆盖物非常相似

对于视频覆盖物只需要：

- 使用 `L.VideoOverlay` 而不是 `L.ImageOverlay`
- `L.VideoOverlay` 用于在地图的特定边界上加载和显示视频播放器。 拓展 [`L.ImageOverlay`](/reference.html#imageoverlay). 
视频覆盖物使用 [`<video>`](https://developer.mozilla.org/docs/Web/HTML/Element/video) 标签。
- 指定一个视频URL **或** 一组视频URL，而不是图像URL

```
var videoUrls = [
	'https://www.mapbox.com/bites/00188/patricia_nasa.webm',
	'https://www.mapbox.com/bites/00188/patricia_nasa.mp4'
];
var errorOverlayUrl = 'https://cdn-icons-png.flaticon.com/512/110/110686.png';
var latLngBounds = L.latLngBounds([[32, -130], [13, -100]]);

var videoOverlay = L.videoOverlay(videoUrls, latLngBounds, {
	opacity: 0.8,
	errorOverlayUrl: errorOverlayUrl,
	interactive: true,
	autoplay: true,
	muted: true,
	playsInline: true
}).addTo(map);
```

就这样，你会在地图上看到视频：

{% include frame.html url="example-nocontrols.html" %}

- `autoplay` 选项定义加载时视频是否自动开始播放。默认是 `true` 。 重要的是要知道，在某些浏览器上 `autoplay` 功能仅适用于 `muted` 选项显式设置为 `true`.

- `muted` 选项定义加载时视频是否以静音方式启动。默认是 `false`。

- `playsInline` 选项设置为 `true` 允许视频以内联方式播放，而不会在移动浏览器中开始播放时自动进入全屏模式。 默认是 `true` .

您可以找到的其他选项 `L.videoOverlay` 在 [documentation](/reference.html#videooverlay).

视频覆盖物图层和其他Leaflet图层类似 - 可以添加或移除，可以让用户通过 [layers control](../layers-control/)来来从几个视频中选择，等等。



#### 对视频的控制

如果你阅读过文档，你就会发现 `L.VideoOverlay` 类并没有 `play()` 或者 `pause()` 方法。

对此， 视频覆盖物的 `getElement()` 方法是有用的。 它返回 [`HTMLVideoElement`](https://developer.mozilla.org/docs/Web/API/HTMLImageElement) (继承自 [`HTMLMediaElement`](https://developer.mozilla.org/docs/Web/API/HTMLMediaElement)) 对于覆盖物 - 就像 `play()` 和 `pause()` 一样，等等。

```
videoOverlay.getElement().pause();
```

这使我们能够构建自定义接口。例如，我们可以构建一个 `L.Control` 的小子类，以便在加载后播放/暂停此视频覆盖物：

```
videoOverlay.on('load', function () {
	var MyPauseControl = L.Control.extend({
		onAdd: function() {
			var button = L.DomUtil.create('button');
			button.title = 'Pause';
			button.innerHTML = '<span aria-hidden="true">⏸</span>';
			L.DomEvent.on(button, 'click', function () {
				videoOverlay.getElement().pause();
			});
			return button;
		}
	});
	var MyPlayControl = L.Control.extend({
		onAdd: function() {
			var button = L.DomUtil.create('button');
			button.title = 'Play';
			button.innerHTML = '<span aria-hidden="true">▶️</span>';
			L.DomEvent.on(button, 'click', function () {
				videoOverlay.getElement().play();
			});
			return button;
		}
	});

	var pauseControl = (new MyPauseControl()).addTo(map);
	var playControl = (new MyPlayControl()).addTo(map);
});
```

{% include frame.html url="example-video.html" %}

### `SVGOverlay`

`L.SVGOverlay`用于在地图的特定边界上加载、显示和提供对SVG文件的DOM访问。
 

添加SVG覆盖 [`L.SVGOverlay`](/reference.html#svgoverlay) 使用这个:

```
var svgOverlay = L.svgOverlay(SVGElement, svgElementBounds, options);
```

它实例化一个给定SVG元素及其绑定的地理边界的图像覆盖对象。SVG元素上需要viewBox属性才能正确放大和缩小。

#### 创建SVG元素

让我们创建一个SVG元素：

```
var svgElement = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
svgElement.setAttribute('xmlns', 'http://www.w3.org/2000/svg');
svgElement.setAttribute('viewBox', '0 0 200 200');
svgElement.innerHTML = '<rect width="200" height="200"/><rect x="75" y="23" width="50" height="50" style="fill:red"/><rect x="75" y="123" width="50" height="50" style="fill:#0013ff"/>';
```

或者，您可以在HTML代码中创建SVG元素：

```
<svg id="svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><rect width="200" height="200"/><rect x="75" y="23" width="50" height="50" style="fill:red"/><rect x="75" y="123" width="50" height="50" style="fill:#0013ff"/></svg>
```

并使用 querySelector 选择此SVG元素：

```
var svgElement = document.querySelector('#svg');
```

#### 添加SVG覆盖物

使用与ImageOverlay和VideoOverlay类似的所需选项创建SVGOverlay：

```
var latLngBounds = L.latLngBounds([[32, -130], [13, -100]]);
map.fitBounds(latLngBounds);

var svgOverlay = L.svgOverlay(svgElement, latLngBounds, {
	opacity: 0.7,
	interactive: true
}).addTo(map);
```

虽然SVGOverlay没有自己独特的选项，但它继承了ImageOverlay、Interactive layer和layer的各种选项。
查看文档 [`L.SVGOverlay`] (/reference.html#svgoverlay)以了解更多信息 

{% include frame.html url="example-svg.html" %}
