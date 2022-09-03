---
layout: tutorial_v2
title: Quick Start Guide
---

## Leaflet 快速入门指南

这个循序渐进的入门指南将会帮助你快速了解 Leaflet 基础知识，包括设置 Leaflet 地图、使用标记、折线和弹出窗口，以及处理事件。

{% include frame.html url="example.html" %}

### 准备一个新的页面

在为地图编写代码之前，你需要在你的页面上完成以下准备步骤：

 * 在文档的 head 部分引入 Leaflet CSS 文件:

		<link rel="stylesheet" href="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.css"
		  integrity="{{site.integrity_hash_css}}"
		  crossorigin=""/>

 * 在引入 Leaflet CSS 文件**之后**引入 Leaflet JavaScript 文件:

		<!-- Make sure you put this AFTER Leaflet's CSS -->
		<script src="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.js"
		  integrity="{{site.integrity_hash_uglified}}"
		  crossorigin=""></script>

 * 将具有特定 `id` 的 `div` 元素放置在你希望地图所在的位置:

		<div id="mapid"></div>

 * 确保地图容器定义了固定高度，例如在 CSS 中设置:

	<pre><code class="css">#mapid { height: 180px; }</code></pre>

现在您已准备好初始化地图并使用它做一些事情。


### 设置地图


{% include frame.html url="example-basic.html" %}

让我们用漂亮的 Mapbox Streets 瓦片（Tile）底图创建一张伦敦市中心的地图。首先，我们将初始化地图并将其视图设置为我们选择的地理坐标和缩放级别：

	var map = L.map('map').setView([51.505, -0.09], 13);

默认情况下（因为我们在创建地图实例时没有传递任何选项），地图上的所有鼠标和触摸交互都处于启用状态，并且具有缩放和属性控制。

请注意，`setView` 调用还会返回地图对象——大多数 Leaflet 方法在不返回显式值时的行为都是这样的，这允许你可以很方便的进行类似 jQuery 的链式调用。

接下来我们将添加一个瓦片（Tile）图层到地图中, 在当前示例中它是一个 OpenStreetMap 瓦片图层。创建一个瓦片（Tile）图层通常会涉及为瓦片（Tile）图像、归属文本和图层的最大缩放级别设置 [URL 模板](/reference.html#tilelayer-url-template)。OpenStreetMap 的瓦片对于你的 Leaflet 地图的编程是没有问题的，但是如果你要在生产中使用瓦片，请阅读 OpenStreetMap 的[瓦片使用政策](https://operations.osmfoundation.org/policies/tiles/)。

<pre><code class="javascript">L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	maxZoom: 19,
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
}).addTo(map);</code></pre>

确保引入 `leaflet.js` 文件并配置好 `div` 后运行所有代码。就是这样，你现在拥有一个运行正常的 Leaflet 地图。

值得注意的是，Leaflet 是与供应商无关的，也就是说，它不会为瓦片（Tile）强制选择一个特定的供应商。而且，Leaflet 甚至不包含任何一行特定于某个供应商的代码，所以如果你需要，你可以自由地使用其他供应商。

根据[版权声明](https://www.openstreetmap.org/copyright)，无论任何时候使用任何基于OpenStreetMap 的东西，署名都是必须的。大多数其他瓦片供应商（如[Mapbox](https://docs.mapbox.com/help/how-mapbox-works/attribution/), [Stamen](http://maps.stamen.com/)或[Thunderforest](https://www.thunderforest.com/terms/)）也需要署名，请确保给予他们应有的荣誉。


### 标记、圆和多边形

{% include frame.html url="example-overlays.html" %}


除了瓦片（Tile）图层，您还可以轻松地向地图添加其他内容，包括标记、折线、多边形、圆形和弹出窗口。让我们添加一个标记：

	var marker = L.marker([51.5, -0.09]).addTo(map);

可以使用同样的方式添加一个圆（除了指定以米为单位的半径作为第二个参数），但允许您通过在创建对象时将选项作为最后一个参数传递来控制它的外观：

	var circle = L.circle([51.508, -0.11], {
		color: 'red',
		fillColor: '#f03',
		fillOpacity: 0.5,
		radius: 500
	}).addTo(map);

添加多边形同样简单：

	var polygon = L.polygon([
		[51.509, -0.08],
		[51.503, -0.06],
		[51.51, -0.047]
	]).addTo(map);


### 使用 popups

{% include frame.html url="example.html" %}

当您想将某些信息附加到地图上的特定对象时，通常会使用 Popups。Leaflet 有一个快捷方式：

	marker.bindPopup("<b>Hello world!</b><br>I am a popup.").openPopup();
	circle.bindPopup("I am a circle.");
	polygon.bindPopup("I am a polygon.");

尝试点击我们的对象。该 `bindPopup` 方法将带有指定 HTML 内容的弹出窗口附加到您的标记，以便在您单击对象时显示弹出窗口，并且该 `openPopup` 方法（仅适用于标记）立即打开附加的弹出窗口。

您还可以将弹出窗口用作图层（当您需要的不仅仅是将弹出窗口附加到对象时）：

	var popup = L.popup()
		.setLatLng([51.513, -0.09])
		.setContent("I am a standalone popup.")
		.openOn(map);

这里我们使用 `openOn` 而不是 `addTo` 因为它在打开一个新窗口时，先前打开的弹出窗口会自动关闭。


### 处理事件

每次在 Leaflet 中触发某些事件时，例如用户单击标记或地图缩放更改，相应的对象都会发送一个事件，您可以使用函数订阅该事件。它允许您对用户交互做出反应：

	function onMapClick(e) {
		alert("You clicked the map at " + e.latlng);
	}

	map.on('click', onMapClick);

每个对象都有属于自己的一组事件——详情请参阅[文档](/reference.html)。监听器、函数的第一个参数是一个事件对象——它包含关于发生的事件的有用信息。例如，地图点击事件对象（在上面的例子中的`e`）有一个 `latlng` 属性，它是点击发生的位置。

让我们通过使用 `popup` 而不是 `alert` 来改进我们的示例：

	var popup = L.popup();

	function onMapClick(e) {
		popup
			.setLatLng(e.latlng)
			.setContent("You clicked the map at " + e.latlng.toString())
			.openOn(map);
	}

	map.on('click', onMapClick);

尝试单击地图，您将在弹出窗口中看到坐标。 <a target="_blank" href="example.html">查看完整示例 &rarr;</a>

现在您已经学习了 Leaflet 的基础知识，可以立即开始构建地图应用程序了！ 不要忘记查看详细 <a href="/reference.html">文档</a> 或 <a href="../../examples.html">其它示例</a>。
