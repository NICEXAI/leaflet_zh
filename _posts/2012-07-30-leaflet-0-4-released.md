---
layout: post
title: Leaflet 0.4 发布
description: 经过 5.5 个月的开发，涉及 33 个贡献者，我很自豪地宣布 Leaflet 0.4 的发布！它带有更简单的 API 和许多重大改进，以及对文档的重大更新、插件页面和开发者博客的发布
author: Vladimir Agafonkin
authorsite: http://agafonkin.com/en
---

经过 5 个半月的开发，从上一个稳定版开始，有 [33 个贡献者](https://github.com/Leaflet/Leaflet/graphs/contributors?from=2012-02-15&to=2012-07-30&type=c) 参与，我很自豪地宣布 Leaflet 0.4 的发布！它有更简单的 API 和*大量*的改进和重要的 bug 修复，还有一个重要的文档更新，一个官方插件页面和这个开发者博客的发布。让我们逐一看一下这些改进。

### 更简单的 API

Leaflet 0.4 包含了一些 API 改进，使你可以写出更简单、更简洁的代码（ [jQuery](http://jquery.com)——like），同时向后兼容以前的方法（这样你就可以使用两种风格）。

	L.marker([51.5, -0.09])
    	.addTo(map)
    	.bindPopup('Hello world!')
    	.openPopup();

首先，Leaflet 方法现在接受 [LatLng][]、[LatLngBounds][]、[Point][] 和 [Bounds][] 对象的简单数组形式，所以你不需要总是明确地创建它们：
 
	map.panTo([50, 30]); // the same as:
	map.panTo(new L.LatLng(50, 30));

第二，像 [addLayer][]、[addControl][]、[openPopup][] 这样的 Map 方法从另一边得到了对应的方法：

	marker.addTo(map);  // same as map.addLayer(marker)
	control.addTo(map); //         map.addControl(control)
	popup.openOn(map);  //         map.openPopup(popup)

再加上所有没有明确返回值的 Leaflet 方法都会返回对象本身，这就使得方法链的使用更加方便。

第三，Leaflet 类现在带有小写的快捷方式（类工厂），允许你在没有 <code>new</code> 关键字的情况下创建对象，这使得链式代码看起来更漂亮：

	L.map('map').fitWorld(); // same as
	(new L.Map('map')).fitWorld();

### 值得注意的新功能

<div id="map" class="map" style="height: 250px"></div>

#### 改进的缩放动画

标记、弹出窗口、矢量图层和图像叠加在以前的版本中是隐藏的，但现在（感谢 [Dave Leaver][] ）它们都有漂亮、流畅的缩放动画，与现有的任何其他地图库不同。试着在上面的地图上进行缩放，看看它看起来如何 如果你在地图上有成千上万的标记，你可以用地图的 `markerZoomAnimation` 选项关闭标记动画，如果它变得很慢。

此外，现在如果你快速放大或缩小一次以上，瓷砖就不会消失。

#### 键盘导航

在 0.4 版本中，Leaflet 地图通过新的键盘处理程序（由 [Eric Martinez](https://github.com/ericmmartinez) 贡献）得到了一个很好的可访问性提升，默认情况下是启用的。它允许用户通过使用方向键平移和 <code>+</code> <code>-</code> 键缩放来浏览地图（在通过标签或点击地图使其成为焦点后）。在上面的地图上试一下，感觉非常好!
 
#### 平移惯性

另一个很好的改进来自于平移体验——————现在它有一个惯性移动效果，在快速平移之后，地图会平稳地继续移动。在触摸设备上感觉特别自然——————而且它也是默认启用的，现在就试试吧! 它也是高度可配置的，允许你设置效果的最大速度、减速度和触发的时间阈值。

#### 安卓 4 上的捏合缩放

在以前的 Leaflet 版本中，捏合缩放只在 iOS 设备上工作，但现在它终于来到了 Android ! 在安卓 4+ 系统中，不仅可以在原版浏览器中使用，还可以在 Chrome 和 Firefox for Android 中使用。

#### 比例控制

一个简单的、轻量级的控件，它以公制和/或英制显示当前地图视图的比例。像往常一样，你可以用 CSS 自定义其外观。看一下上面地图的左下角吧！

	L.control.scale().addTo(map);

#### 多段线和多边形编辑

允许用户用一个简单、直观的界面来编辑折线和多边形。请注意，这个功能最终会并入 [Leaflet.draw][] —————— 一个由 Jacob Toye 开发的用于绘制形状的很棒的插件。

	polygon.editing.enable();

#### 基于 Div 的图标

除了基于图像的 [Icon][] 类，Leaflet 0.4 还获得了一个 [DivIcon][] 类，用于创建轻量级的基于 div 的标记（可以包含自定义 HTML 并可以用 CSS 进行样式设计）。例如，你可以在编辑多段线时看到它们的作用（方形手柄），或者在我稍后要讲的 [Leaflet.markercluster][] 插件中（彩色的集群）。

	L.marker([50.505, 30.57], {
		icon: L.divIcon({className: 'my-div-icon'})
	}).addTo(map);

#### 矩形层

矩形是创建矩形区域图层的一个方便的快捷方式。你可以在前面用多边形做这个，但这更容易：

	L.rectangle([[51.505, -0.03], [51.5, -0.045]]).addTo(map);

### API 改进

#### GeoJSON API

[GeoJSON][] API 得到了改进，变得更加简单和灵活。[Jason Sanford][] 写了一个 [伟大的教程](.../.../.../examples/geojson.html) ，展示了新的 API 。不过这些变化并不向后兼容，所以一定要更新你的旧代码。

#### 图标 API

[Icon][] API 被改进得更简单、更灵活，而且这些变化也不是向后兼容的（尽管旧代码可以很快被更新）。看看更新后的 [自定义图标教程](.../.../.../examples/custom-icons.html) ，或者直接前往 [API文档](.../.../reference.html#icon) 。
 
#### 控件 API

自定义控件现在更容易创建了——————请查看 [API docs](./././reference.html#icontrol) ，其中也有一个简单的例子。

#### 更好的事件 API

[Aaron King][] 给 [事件方法](./././reference.html#events) 带来一些改进。 `on` 和 `off` 方法现在可以同时接受多个事件类型，作为一个空格分隔的字符串类型：

	map.on('click dblclick moveend', doStuff);

另外，它们可以接受一个带有类型和监听器功能的对象作为键 / 值对，像这样。

	marker.on({
		click: onMarkerClick,
		dragend: onMarkerDragEnd
	});

此外，现在如果你只指定一个事件类型给 `off` 方法，它将删除所有与此事件绑定的监听器。

	map.off('click');

#### 其他 API 的改进

Leaflet 0.4 在不同的 Leaflet 类中有 30 多个新方法、选项和事件，使 API 更加完整和强大。请查看 [完整的更新日志](https://github.com/Leaflet/Leaflet/blob/master/CHANGELOG.md#other-api-improvements) 以了解完整的列表。

### 性能和易用性的改进

你可能认为 Leaflet 已经快得令人难以置信了，但这个版本带来了一些性能上的改进，使它变得更快。

 * 平移、调整地图大小和捏合缩放的性能得到了改善（这背后的一些技巧将在未来的博文中解释）。
 * 在画布后端更新和删除矢量图层（例如在安卓 2 上）的工作速度要快很多倍。
 * 在移动设备上，控件上的盒状阴影被替换为简单的边框，以提高性能。
 * 矢量图层现在在 iOS 上每次平移后都不会闪烁了。

此外，还有一些尚未提及的可用性改进：

 * 即使光标下有标记，平移现在也能工作（对拥挤的地图有帮助）。
 * 弹出窗口外观略有改进。
 * 瓦片层现在有 <code>detectRetina</code> 选项，启用后会将瓦片的分辨率提高一倍，以适应视网膜显示器（由 [Mithgol][] 贡献）。

### 错误修复

Leaflet 0.4 带来了大约 45 个 bug 修复，使其在所有的浏览器和平台上更加稳定和可靠。值得注意的 bug 修复包括可怕的 iOS bug ，该 bug 在某些罕见的情况下会导致地图在捏合缩放后完全消失，在 IE10 测试版上缩放失败，在 XHTML 内容类型的页面上 Leaflet 地图失败，以及在固定位置元素内的地图缩放不正确。
 
下面是更新日志中的 [错误修复的完整列表](https://github.com/Leaflet/Leaflet/blob/master/CHANGELOG.md#bug-fixes) 。

### 从旧版本升级

除了上面提到的 GeoJSON 和 Icon 的变化，这里还有一个 [潜在的破坏性变化列表](https://github.com/Leaflet/Leaflet/blob/master/CHANGELOG.md#other-breaking-api-changes) —————— 在更新你的代码时，请仔细阅读它（虽然不应该花太多时间）。

Leaflet 0.4 的下载选项（包括实际下载，CDN 托管的版本，以及手动构建的说明）在 [下载页面](.../.../.../download.html) 列出。

### 代码统计

我仍然致力于使 Leaflet 尽可能的小而轻。下面是目前库的大小分类：

 * JavaScript: **27 KB** ，已压缩和 gzipped (102 KB minified, 176 KB in source, 7578 lines of code)
 * CSS: **1.8 KB** gzipped (8 KB, 377 lines of code)
 * Images: **10 KB** (5 PNG images)

### 文档更新

到目前为止，Leaflet 的 API 参考是不完整的。但在这个版本中，我们付出了巨大的努力，使其成为 100% 完整的、最新的、通常是你所见过的最好的 API 参考页面。所有剩余的类、方法、选项、事件和属性都被仔细记录下来，并添加了更多的代码实例，从现在开始，文档将一直保持更新。

此外，页面的设计也得到了显著的改善 —————— 有更好的颜色、字体、间距、连字符、手动调整的列宽等等。

### 插件页面

Leaflet 网站现在有一个官方的 [插件页面](.../.../.../plugins.html) ，列出了许多 Leaflet 插件，这些插件是由令人敬畏的 Leaflet 社区创建的，增加了许多伟大的功能，有助于服务的整合。

我想提到的一个插件是 [Dave Leaver] 的 [Leaflet.markercluster][] ，目前是我见过的所有地图库中最好的标记聚类插件 —————— 它快速、漂亮，为聚类提供流畅的动画，包括一个智能的谷歌地球式的解决方案，用于在最后一个缩放级别上拥挤的标记（由 [George MacKerron][] ），可以在悬停时突出一个集群所覆盖的区域，在移动设备上工作良好，并且可以轻松地进行定制。我想我们会在下一篇文章中更详细地介绍这个插件。

另一个值得注意的插件是 [Jacob Toye][] 的 [Leaflet.draw][] ，灵感来自 [Bruno B](https://github.com/brunob) 的一个类似插件。它通过一个非常好的带有图标和提示的用户友好界面，实现了多段线、多边形、矩形、圆和标记等绘画功能。其他与编辑有关的代码可能会在将来移入这个插件。

另外，由于 [Kartena](http://www.kartena.se/) 的 [Proj4Leaflet](https://github.com/kartena/Proj4Leaflet) 插件，GIS 爱好者现在可以享受 Leaflet 的一些古怪和罕见的投影的地图。

还有一个基于 Leaflet 的创作，每个人都需要看看 [OSM Buildings](http://flyjs.com/buildings/) by [Jan Marsch](http://flyjs.com/buildings/about.php) ，一个惊人的 JS 库，用于在 Leaflet 地图上可视化 3D OSM 建筑数据。令人难以置信的酷东西。

### 开发者博客

这是官方 Leaflet 开发者博客的第一篇文章，它将成为所有与 Leaflet 相关的重要新闻、教程、技巧和开发说明的主要场所。

### 使用 Leaflet 的大公司

自从上次发布后，Leaflet 被许多伟大的公司采用，包括 [Flickr](http://flickr.com/map) ，[foursquare](http://foursquare.com) 和 [Wikimedia Foundation](http://blog.wikimedia.org/2012/04/05/new-wikipedia-app-for-ios-and-an-update-for-our-android-app/)（现在在 [frontpage](./././index.html) 中出现）。对于 Leaflet 和开源地图来说，这是一个非常激动人心的时刻，我期待着看到许多其他公司在未来跟随这一令人敬畏的趋势。

### 谢谢你

我想感谢所有帮助 Leaflet 成为现在这样的人 —————— 贡献代码、报告错误、在他们的网站上使用 Leaflet、向同事介绍它、在会议上谈论它，等等。继续努力吧!

特别感谢 [Dave Leaver][] 的鼓舞人心的贡献，包括改进的缩放动画和最先进的集群插件，以及 [Jason Sanford][] 的友好支持（以及建立 Leaflet CDN 和其他事情）。

当然，还要感谢我那家了不起的公司，[CloudMade](http://cloudmade.com) ，感谢他们拥抱开源并支持这一发展。

Sincerely, <br />
Vladimir Agafonkin, Leaflet maintainer.

 [LatLng]: ../../../reference.html#latlng
 [LatLngBounds]: ../../../reference.html#latlngbounds
 [Point]: ../../../reference.html#point
 [Bounds]: ../../../reference.html#bounds
 [Icon]: ../../../reference.html#icon
 [DivIcon]: ../../../reference.html#divicon
 [GeoJSON]: ../../../reference.html#geojson

 [addControl]: ../../../reference.html#map-addcontrol
 [addLayer]: ../../../reference.html#map-addlayer
 [openPopup]: ../../../reference.html#map-openpopup

 [Leaflet.draw]: https://github.com/jacobtoye/Leaflet.draw
 [Leaflet.markercluster]: https://github.com/danzel/Leaflet.markercluster

 [Dave Leaver]: https://github.com/danzel
 [Jason Sanford]: https://github.com/JasonSanford
 [Aaron King]: https://github.com/Guiswa
 [Mithgol]: https://github.com/Mithgol
 [George MacKerron]: https://github.com/jawj/
 [Jacob Toye]: https://github.com/jacobtoye

<script>
	var map = L.map('map').setView([51.503, -0.09], 13);

	L.tileLayer(MB_URL, {attribution: MB_ATTR, id: 'examples.map-i875mjb7'}).addTo(map);

	var polygon = L.polygon([
		[51.509, -0.08],
		[51.503, -0.06],
		[51.51, -0.047]
	], {color: 'red'}).addTo(map).bindPopup('I am an editable polygon.');

	polygon.editing.enable();

	L.control.scale().addTo(map);

	L.marker([51.5, -0.095]).addTo(map)
		.bindPopup("<b>Hello world!</b><br />I am a popup.").openPopup();

	L.marker([51.505, -0.115]).addTo(map).bindPopup("I am a second popup.");
	L.marker([51.496, -0.13]).addTo(map).bindPopup("I am a third popup.");

	L.rectangle([
		[51.505, -0.03],
		[51.5, -0.045]
	], {weight: 1, opacity: 0.8}).addTo(map).bindPopup('I am a rectangle.');
</script>
