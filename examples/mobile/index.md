---
layout: tutorial_v2
title: Leaflet on Mobile
---

## 在移动端使用 Leaflet

在本教程中，你将学习如何为 iPhone、iPad 或 Android 手机等移动设备创建一个全屏地图，以及如何轻松检测和使用当前的用户位置。

{% include frame.html url="example.html" %}

### Preparing the page

首先，我们来看一下页面的 HTML 和 CSS 代码。为了让我们的地图 `div` 元素拉伸到所有可用空间（全屏），我们可以使用下面的 CSS 代码（注意：在这个例子中，我们使用百分比作为高度。虽然 vh 可以说更好，但是在移动设备上的谷歌浏览器存在问题）：

{: .css}
	body {
		padding: 0;
		margin: 0;
	}
	html, body, #map {
		height: 100%;
		width: 100vw;
	}

此外，我们需要通过在 `head` 部分或我们的 HTML 页面中放置以下内容来告诉移动浏览器禁用页面缩放并将其设置为实际大小：

	<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />

### 初始化地图

我们现在将在 JavaScript 代码中初始化地图，就像我们在[快速入门指南](../quick-start/)中所做的那样，显示整个世界地图：

<pre><code class="javascript">var map = L.map('map').fitWorld();

L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
	maxZoom: 19,
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);</code></pre>

### 地理位置

Leaflet 有一个非常方便的快捷方式来放大地图视图到检测到的位置---`locate` 方法加上 `setView` 选项，取代了代码中通常的 `setView` 方法:

	map.locate({setView: true, maxZoom: 16});

这里我们指定 16 作为自动设置地图视图时的最大缩放值。只要用户同意分享其位置，并且被浏览器检测到，地图就会将视图设置为它。现在我们有了一个可以工作的全屏移动地图 但是，如果我们需要在地理定位完成后做一些事情呢？这就是 `locationfound` 和 `locationerror` 事件的作用。例如，让我们在检测到的位置上添加一个标记，在弹出式窗口中显示精确度，在 `locateAndSetView` 调用之前给 `locationfound` 事件添加一个事件监听器:

	function onLocationFound(e) {
		var radius = e.accuracy;

		L.marker(e.latlng).addTo(map)
			.bindPopup("You are within " + radius + " meters from this point").openPopup();

		L.circle(e.latlng, radius).addTo(map);
	}

	map.on('locationfound', onLocationFound);

非常好! 但如果能在地理定位失败时显示错误信息，那就更好了:

	function onLocationError(e) {
		alert(e.message);
	}

	map.on('locationerror', onLocationError);

如果你把 `setView` 选项设置为 "true"，并且地理定位失败，它将把视图设置为整个世界。

现在，这个例子已经完成了---在你的手机上试试吧。[查看完整的示例&rarr;](example.html)

下一步可以查看详细的[文档](/reference.html)和浏览[其它示例](../../examples.html)。
