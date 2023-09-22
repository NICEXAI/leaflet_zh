---
layout: tutorial_v2
title: Overlays
---

## Overlays

在 Leaflet API 中有三种 overlays ：

- [`ImageOverlay`](/reference.html#imageoverlay): 栅格图层，扩展自 [`Layer`](/reference.html#layer)
- [`VideoOverlay`](/reference.html#videooverlay): 栅格图层，扩展自 [`ImageOverlay`](/reference.html#imageoverlay)
- [`SVGOverlay`](/reference.html#svgoverlay): 矢量图层，扩展自 [`ImageOverlay`](/reference.html#imageoverlay)

在本教程中，您将学习如何使用这三种 overlays 。

### `ImageOverlay`

`L.ImageOverlay` 被用于在地图的特定边界上加载和显示单个图像。 

使用 [`L.ImageOverlay`](/reference.html#imageoverlay) 添加一个图像覆盖物：

```
var imageOverlay = L.imageOverlay(imageUrl, latLngBounds, options);
```

#### 创建一个地图


首先，创建一个 Leaflet 地图并且通过 `L.TileLayer` 添加常用底图：
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

如果您想查看 ImageOverlay 覆盖物的区域，可以将具有相同 `L.LatLngBounds` 的 [`L.Rectangle`](reference.html#rectangle) 添加到地图中：

```
L.rectangle(latLngBounds).addTo(map);
map.fitBounds(latLngBounds);
```

- `opacity` 定义图像覆盖物的不透明度，默认是 `1.0`。减小该值可以使图像覆盖物透明，从而暴露出下面的图层。  
	
- `errorOverlayUrl` 需要显示的图像覆盖物的URL，以代替加载失败的覆盖物。

- `alt` 设置HTML属性，[`alt`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-alt) 提供替代图像的描述。替代文本同样也是屏幕阅读器用户的基本信息。它可以在网络连接不良的情况下为人们带来好处。此外，它还可以提高网站的SEO。

- `interactive` 默认是 `false`。如果改为 `true`，图像覆盖物将会响应鼠标的点击或悬浮事件。

您可以找到 `L.ImageOverlay` 的其他参数在 [documentation](/reference.html#imageoverlay) 中。

{% include frame.html url="example-image.html" %}

### `VideoOverlay`

在 [`<video>` HTML element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video) 出现之前的网页构建中，视频的应用是一项艰难的任务。

但是现在，我们可以使用以下 HTML 代码：

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

如果视频可以用这种方式展示在网页上，那么 Leaflet 也可以如此运用在地图上。重要的是，我们所准备的视频应适合地图：视频应朝向“北上”方向，并且比例合适。如果没有，它将看起来不舒服。

#### 创建一个地图

首先，创建一个 Leaflet 地图并且通过 `L.TileLayer` 添加常用底图：

```
var map = L.map('map').setView([37.8, -96], 4);

var osm = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
	maxZoom: 19,
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);
```

#### 添加视频覆盖物

添加视频覆盖物的内容与和添加图像覆盖物非常相似。

对于视频覆盖物您只需要：

- 使用 `L.VideoOverlay` 而不是 `L.ImageOverlay`。
- `L.VideoOverlay` 用于在地图的特定边界上加载和显示视频播放器。拓展自 [`L.ImageOverlay`](/reference.html#imageoverlay)
的视频覆盖物使用 [`<video>`](https://developer.mozilla.org/docs/Web/HTML/Element/video) 标签。
- 指定一个视频 URL **或** 一组视频 URL，而不是图像 URL。

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

就这样，您将会在地图上看到视频：

{% include frame.html url="example-nocontrols.html" %}

- `autoplay` 选项定义加载时，视频是否自动开始播放。默认是 `true` 。更重要的是要知道，在某些浏览器上 `autoplay` 功能仅适用于 `muted` 选项显式设置为 `true` 时。

- `muted` 选项定义加载时，视频是否以静音方式启动。默认是 `false`。

- `playsInline` 选项设置为 `true` 时，允许视频以内联方式播放，而不会在移动浏览器中开始播放时自动进入全屏模式。默认是 `true` 。

您可以找到 `L.videoOverlay` 的其他选项在 [documentation](/reference.html#videooverlay) 中。

视频覆盖物和其他 Leaflet 图层类似 —— 您可以添加或移除它们，也可以让用户通过 [layers control](../layers-control/) 从几个视频中选择。



#### 对视频的控制

如果您阅读过 API 文档，您就会注意到 `L.VideoOverlay` 类中并没有 `play()` 或者 `pause()` 方法。

对此，视频覆盖物的 `getElement()` 方法是十分有用的。 对于覆盖物来说，它返回 [`HTMLVideoElement`](https://developer.mozilla.org/docs/Web/API/HTMLImageElement) (继承自 [`HTMLMediaElement`](https://developer.mozilla.org/docs/Web/API/HTMLMediaElement)) —— 并且它的方法就像 `play()` 和 `pause()` 一样。

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

`L.SVGOverlay` 用于在地图的特定边界上加载、显示和提供对 SVG 文件的 DOM 访问。
 

[`L.SVGOverlay`](/reference.html#svgoverlay) 可以这样添加 SVG 覆盖物:

```
var svgOverlay = L.svgOverlay(SVGElement, svgElementBounds, options);
```

它实例化一个给定 SVG 元素并且有确定地理边界的图像覆盖物对象。对于SVG 元素来说，viewBox 属性必须存在它才能正确的放大和缩小。

#### 创建一个 SVG 元素

让我们创建一个 SVG 元素：

```
var svgElement = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
svgElement.setAttribute('xmlns', 'http://www.w3.org/2000/svg');
svgElement.setAttribute('viewBox', '0 0 200 200');
svgElement.innerHTML = '<rect width="200" height="200"/><rect x="75" y="23" width="50" height="50" style="fill:red"/><rect x="75" y="123" width="50" height="50" style="fill:#0013ff"/>';
```

或者，您可以在 HTML 代码中创建 SVG 元素：

```
<svg id="svg" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><rect width="200" height="200"/><rect x="75" y="23" width="50" height="50" style="fill:red"/><rect x="75" y="123" width="50" height="50" style="fill:#0013ff"/></svg>
```

并使用 querySelector 来选择这个 SVG 元素：

```
var svgElement = document.querySelector('#svg');
```

#### 添加 SVG 覆盖物

创建 SVGOverlay 所需的选项与 ImageOverlay 和 VideoOverlay 类似：

```
var latLngBounds = L.latLngBounds([[32, -130], [13, -100]]);
map.fitBounds(latLngBounds);

var svgOverlay = L.svgOverlay(svgElement, latLngBounds, {
	opacity: 0.7,
	interactive: true
}).addTo(map);
```

虽然 SVGOverlay 没有自己独特的选项，但是它继承了 ImageOverlay、Interactive layer 和 layer 的各种选项。
查看文档 [`L.SVGOverlay`](/reference.html#svgoverlay) 可以了解更多选项 。

{% include frame.html url="example-svg.html" %}
