---
layout: tutorial_v2
title: Zoom levels
---

<style>
.tiles img {
    border: 1px solid #ccc;
    border-radius: 5px;
    margin: 5px;
}
.tiles.small img {
    border: 1px solid #ccc;
    border-radius: 5px;
    margin: 1px;
    width: 64px;
    height: 64px;
}
.tiles {
    line-height: 0;
}
.tiles.legend {
    line-height: 1;
}
</style>

## Zoom levels

Leaflet 适用于 [latitude](https://en.wikipedia.org/wiki/Latitude), [longitude](https://en.wikipedia.org/wiki/Longitude) 和 "zoom level"。

较低的缩放比例意味着地图可以显示整个大陆，而较高的缩放比例意味着地图可以显示一个城市的细节。

要了解 `zoom levels` 工作原理，首先我们需要对 <i>geodesy</i> 进行基本介绍。

## 地球的形状

让我们来看一张缩放比例为零的简单地图：

	var map = L.map('map', {
		minZoom: 0,
		maxZoom: 0
	});

	var cartodbAttribution = '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, &copy; <a href="https://carto.com/attribution">CARTO</a>';

	var positron = L.tileLayer('https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png', {
		attribution: cartodbAttribution
	}).addTo(map);

	map.setView([0, 0], 0);

{% include frame.html url="example-zero.html" %}

请注意，**整个地球**只是一张图像，宽 256 像素，高 256 像素：

<div class='tiles' style='text-align: center'>
<img src="https://a.basemaps.cartocdn.com/light_all/0/0/0.png" class="bordered-img" alt=""/>
</div>

我们要明白的是：地球不是一个正方形。相反，地球有一个不规则的形状，可以近似于[类似于球体的东西]（https://en.wikipedia.org/wiki/Geoid）。

所以我们*假设*地球大部分是圆的。为了使它平坦，我们在周围放了一个假想的圆柱体，展开它，然后将其切割成方形：

<div class='tiles legend' style='text-align: center'>
<a title="By derived from US Government USGS [Public domain], via Wikimedia Commons" href="https://en.wikipedia.org/wiki/Map_projection#Cylindrical"><img width="512" alt="Usgs map mercator" src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/Usgs_map_mercator.svg/512px-Usgs_map_mercator.svg.png"/>
<br/>
This is called a "cylindrical map projection".
</a>
</div>

当然这并不是在平面上显示地球表面的唯一方法。 有[数百种方法](https://en.wikipedia.org/wiki/Map_projection)，每一种方法都有自己的优点和缺点。下面这段6分钟的视频很好的介绍了这个主题：

<center><iframe width="696" height="392" src="https://www.youtube.com/embed/kIID5FDi2JQ" frameborder="0" allowfullscreen></iframe></center>

诸如大地测量、地图投影和坐标系之类的事情很难，*非常难* （并且超出了本教程的范围）。假设地球是一个正方形并不总是正确的做法，但大多数情况下都可以正常工作，使事情变得更简单，并且允许 Leaflet（和其他地图库）变得更快。

## Powers of two

现在，让我们**假设**世界是一个正方形：

<div class='tiles' style='text-align: center'>
<img src="https://a.basemaps.cartocdn.com/light_all/0/0/0.png" class="bordered-img" alt=""/>
</div>

当我们以**0**缩放级别表示世界时，它的宽度和高度为 256 像素。当我们进入缩放级别**1**时，它的宽度和高度加倍，可以用四个 256 像素 x 256 像素的图像表示：

<div class='tiles' style='text-align: center'>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/1/0/0.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/1/1/0.png" class="bordered-img" alt=""/>
</div>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/1/0/1.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/1/1/1.png" class="bordered-img" alt=""/>
</div>
</div>

在每个缩放级别，每个图块被分成四份，其大小（边的长度，由 `tileSize` 选项给出）加倍，使面积翻四倍 (换句话说，世界的宽度和高度都是 <code>256·2<sup>zoomlevel</sup></code> 像素):

<table><tr><td>
<div class='tiles small' style='text-align: center'>
<img src="https://a.basemaps.cartocdn.com/light_all/0/0/0.png" class="bordered-img" alt=""/>
</div>
</td><td>
<div class='tiles small' style='text-align: center'>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/1/0/0.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/1/1/0.png" class="bordered-img" alt=""/>
</div>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/1/0/1.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/1/1/1.png" class="bordered-img" alt=""/>
</div>
</div>
</td><td>
<div class='tiles small' style='text-align: center'>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/2/0/0.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/1/0.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/2/0.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/3/0.png" class="bordered-img" alt=""/>
</div>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/2/0/1.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/1/1.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/2/1.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/3/1.png" class="bordered-img" alt=""/>
</div>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/2/0/2.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/1/2.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/2/2.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/3/2.png" class="bordered-img" alt=""/>
</div>
<div>
<img src="https://a.basemaps.cartocdn.com/light_all/2/0/3.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/1/3.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/2/3.png" class="bordered-img" alt=""/><img src="https://a.basemaps.cartocdn.com/light_all/2/3/3.png" class="bordered-img" alt=""/>
</div>
</div>
</td></tr>
<tr><td>Zoom 0</td><td>Zoom 1</td><td>Zoom 2</td></tr></table>

这一直持续下去。大多数瓦片（Tile）服务提供最高缩放级别为 18 的磁贴，具体取决于它们的覆盖范围。这足以让每个瓦片(Tile)看到几个城市街区。

## 关于缩放比例的说明

使用圆柱投影的缺点之一是比例不恒定，测量距离或尺寸不可靠，特别是在低缩放级别时。

在[技术术语](https://en.wikipedia.org/wiki/Map_projection#Projections_by_preservation_of_a_metric_property)中，Leaflet 使用的圆柱投影是共形的（保留形状），但不是等距的（不保留距离），也不是等面积的 （不保留面积，因为赤道附近的东西看起来比它们小）。

通过在地图上添加 `L.Control.Scale`，并平移到赤道和北纬60°，我们可以看到比例尺是如何**翻倍**的。以下示例使用 [javascript timeouts](https://developer.mozilla.org/docs/Web/API/WindowTimers/setTimeout) 自动执行此操作：

	L.control.scale().addTo(map);

	setInterval(function(){
		map.setView([0, 0]);
		setTimeout(function(){
			map.setView([60, 0]);
		}, 2000);
	}, 4000);

{% include frame.html url="example-scale.html" %}

`L.Control.Scale` 显示适用于地图中心点的比例。
在高缩放级别，比例尺的变化很小，并不明显。


## 控制地图缩放

Leaflet 地图有多种方法可以控制显示的缩放级别，但最明显的一种是 [`setZoom()`](/reference.html#map-setzoom)。例如，`map.setZoom(0);` 将缩放级别设置` map` 为 `0`。

这个例子再次使用超时在缩放级别`0`和`1`之间自动交替：

	setInterval(function(){
		map.setZoom(0);
		setTimeout(function(){
			map.setZoom(1);
		}, 2000);
	}, 4000);

{% include frame.html url="example-setzoom.html" %}

请注意缩放级别 0 和 1 显示的图像与上一节中显示的图像是如何对应的！

其他设置缩放的方法有：

* [`setView(center, zoom)`](/reference.html#map-setview), 这也设置了地图中心
* [`flyTo(center, zoom)`](/reference.html#map-flyto), 像`setView`一样，拥有一个平滑的动画
* [`zoomIn()` / `zoomIn(delta)`](/reference.html#map-zoomin), 以 `delta ` 为单位进行放大，默认为 `1`
* [`zoomOut()` / `zoomOut(delta)`](/reference.html#map-zoomout), 以 `delta ` 为单位进行缩小，默认为 `1`
* [`setZoomAround(fixedPoint, zoom)`](/reference.html#map-setzoomaround), 在保持点固定的同时设置缩放级别（滚轮缩放）
* [`fitBounds(bounds)`](/reference.html#map-fitbounds), 自动计算缩放以适应地图上的矩形区域


## Fractional zoom（以分数为单位进行缩放，例如：0.1）

在Leaflet 1.0.0中引入的一个功能是 <em>fractional zoom</em> 的概念。
在这之前，地图的缩放级别只能是一个整数（`0`，`1`，`2`，等等），
但现在你可以使用小数，如`1.5`或`1.25`。

默认情况下，分数缩放是禁用的。要启用它，请使用
[地图的`zoomSnap`选项]（/reference.html#map-zoomsnap）。
`zoomSnap`选项的默认值是`1`（这意味着地图的缩放级别可以是`0`）。
这意味着地图的缩放级别可以是`0`，`1`，`2`，以此类推）。)

如果你把 "zoomSnap "的值设置为 "0.5"，那么地图的有效缩放级别为
将是`0`、`0.5`、`1`、`1.5`、`2`，以此类推。

如果你设置的值是 "0.1"，地图的有效缩放级别将是 "0"、"0.1"。
`0.2`，`0.3`，`0.4`，以此类推。

以下示例使用 `zoomSnap` 值 `0.25`：

	var map = L.map('map', {
		zoomSnap: 0.25
	});

{% include frame.html url="example-fractional.html" %}

如您所见，Leaflet 只会加载缩放级别 `0` 或 `1` 的图块，并根据需要缩放它们。

Leaflet 将 <em>snap</em> 缩放到最接近的有效级别。比如说: 如果你有`zoomSnap: 0.25`，而你试图做`map.setZoom(0.8)`，缩放会 缩回到`0.75`。`map.fitBounds(bounds)` 在结束
触摸屏上的捏合缩放手势时也会发生同样的情况。

`zoomSnap` 可以设置为零。这意味着 Leaflet 将不会捕捉缩放级别。

还有涉及到另一个重要的地图选项 `zoomSnap`：[`zoomDelta` 选项](/reference.html#map-zoomdelta)。这控制了使用缩放按钮（默认为 [`L.Control.Zoom`](/reference.html#control-zoom)）或键盘中的+/-键时要放大/缩小的缩放级别。

对于鼠标滚轮缩放，该 [`wheelPxPerZoomLevel`](/reference.html#map-wheelpxperzoomlevel) 选项控制鼠标滚轮放大或缩小的速度。

这是一个 `zoomSnap` 设置为零的示例：

	var map = L.map('map', {
		zoomDelta: 0.25,
		zoomSnap: 0
	});

尝试以下操作，看看缩放级别如何变化：

* 如果您有触摸屏，请捏合缩放
* 用鼠标滚轮放大/缩小
* 进行框缩放（按住 `shift` 键盘上的键的同时用鼠标拖动）
* 使用放大/缩小按钮

{% include frame.html url="example-delta.html" %}


本教程到此结束。现在，在你的地图中使用缩放比例试试吧！
