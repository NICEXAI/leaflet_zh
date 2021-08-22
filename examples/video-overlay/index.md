---
layout: tutorial_v2
title: Leaflet on Mobile
---

## 在 WEB 页面上显示视频

在构建网页时，显示视频曾经是一项艰巨的任务，直到 [`<video>` HTML 元素](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video)可以使用。

现在，我们可以使用以下 HTML 代码：

	<video width="500" controls>
		<source src="https://www.mapbox.com/bites/00188/patricia_nasa.webm" type="video/webm">
		<source src="https://www.mapbox.com/bites/00188/patricia_nasa.mp4" type="video/mp4">
	</video>

来显示这个视频:

<video width="500" controls>
<source src="https://www.mapbox.com/bites/00188/patricia_nasa.webm" type="video/webm">
<source src="https://www.mapbox.com/bites/00188/patricia_nasa.mp4" type="video/mp4">
</video>

如果一个视频可以通过这种方式在网页中显示，那么 Leaflet 就可以在地图中显示它。重要的是，视频的准备要符合地图的要求。视频应该有一个 "北上 "的方向，其比例应该符合地图的要求。如果不是这样，它就会显得格格不入。

### 图像覆盖的边界

首先，创建一个 Leaflet 地图，并按常规方法使用 `L.TileLayer` 添加一个背景：

	var map = L.map('map').setView([37.8, -96], 4);

	L.tileLayer('https://api.mapbox.com/styles/v1/{id}/tiles/{z}/{x}/{y}?access_token=' + mapboxAccessToken, {
		id: 'mapbox/satellite-v9',
		attribution: ...,
		tileSize: 512,
		zoomOffset: -1
	}).addTo(map);

然后，我们将定义视频将覆盖的地理边界。这是一个 [`L.LatLngBounds`](/reference.html#latlngbounds) 的实例，它是一个矩形：

	var bounds = L.latLngBounds([[ 32, -130], [ 13, -100]]);

如果你想看到 `LatLngBounds` 所覆盖的区域，请使用 [`L.Rectangle`](/reference.html#rectangle)：

	L.rectangle(bounds).addTo(map);

	map.fitBounds(bounds);

{% include frame.html url="example-bounds.html" %}


### 添加视频覆盖图层

添加视频叠加与添加图片叠加的工作非常相似。对于一张图像，[`L.ImageOverlay`s](/reference.html#imageoverlay) 的使用方式如下：

	var overlay = L.imageOverlay( imageUrl, bounds, options );

如果要覆盖一个视频的话, 只需要:

* 使用 `L.videoOverlay` 代替 `L.imageOverlay`
* 指定一个Video URL 或一组 Video URL，而不是 Image URL

```
	var videoUrls = [
		'https://www.mapbox.com/bites/00188/patricia_nasa.webm',
		'https://www.mapbox.com/bites/00188/patricia_nasa.mp4'
	];

	var bounds = L.latLngBounds([[ 32, -130], [ 13, -100]]);

	var videoOverlay = L.videoOverlay( videoUrls, bounds, {
		opacity: 0.8
	}).addTo(map);
```

就像这样，您就可以在地图上看到视频了：

{% include frame.html url="example-nocontrols.html" %}


`videoOverlay` 的行为与其他 Leaflet 层一样--你可以添加和删除它们，让用户使用 [layers control](.../layers-control/) 从几个视频中选择，等等。


### 对视频的添加一些控制

如果你阅读API文档，你会注意到 `L.VideoOverlay` 类没有 `play()` 或 `pause()` 方法。

为此，`videoOverlay` 中的 `getElement()` 方法很有用。它返回覆盖层的 [`HTMLVideoElement`](https://developer.mozilla.org/docs/Web/API/HTMLImageElement)（继承自  [`HTMLMediaElement`](https://developer.mozilla.org/docs/Web/API/HTMLMediaElement)） - 并且具有像 `play()`  和 `pause()` 这样的方法，例如：

```
	videoOverlay.getElement().pause();
```

这使得我们可以建立自定义的接口。例如，我们可以建立一个 `L.Control` 子类，以便在这个 `video overlay` 加载后播放/暂停：

```
	videoOverlay.on('load', function () {
		var MyPauseControl = L.Control.extend({
			onAdd: function() {
				var button = L.DomUtil.create('button');
				button.innerHTML = '⏸';
				L.DomEvent.on(button, 'click', function () {
					videoOverlay.getElement().pause();
				});
				return button;
			}
		});
		var MyPlayControl = L.Control.extend({
			onAdd: function() {
				var button = L.DomUtil.create('button');
				button.innerHTML = '▶️';
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

{% include frame.html url="example.html" %}
