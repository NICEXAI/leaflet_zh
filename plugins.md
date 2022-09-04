---
layout: v2
title: Plugins
bodyclass: plugins-page
---

<style>
table.plugins td > p {
	margin-top: 0;
	margin-bottom: 0;
}
</style>

## Leaflet 插件

Leaflet的目的是尽可能轻巧，并着重于一组核心功能，而扩展其功能的一种简单方法是使用第三方插件。 感谢Leaflet背后的强大社区，提供了数百个不错的插件供大家选择。

---

<div id="toc" class="clearfix">
	<div class="toc-col">
		<h4>Tile &amp; Image 图层</h4>
		<ul>
			<li> <a href='#basemap-providers'>底图提供程序</a></li>
			<li> <a href='#basemap-formats'>底图格式</a></li>
			<li> <a href='#non-map-base-layers'>Non-map 基础图层</a></li>
			<li> <a href='#tileimage-display'>Tile/Image 显示</a></li>
			<li> <a href='#tile-load'>Tile 加载</a></li>
			<li> <a href='#vector-tiles'>矢量 Tile</a></li>
		</ul>
		<h4>Overlay data</h4>
		<ul>
			<li> <a href='#overlay-data-formats'>Overlay data formats</a></li>
			<li> <a href='#dynamiccustom-data-loading'>动态加载数据</a></li>
			<li> <a href='#synthetic-overlays'>Synthetic overlays</a></li>
			<li> <a href='#data-providers'>Data providers 数据提供程序</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>Overlay Display</h4>
		<ul>
			<li><a href="#markers--renderers">Markers &amp; 渲染</a></li>
			<li><a href="#overlay-animations">Overlay 动画</a></li>
			<li><a href="#clusteringdecluttering">Clustering/decluttering</a></li>
			<li><a href="#heatmaps">Heatmaps 热力图</a></li>
			<li><a href="#dataviz">DataViz 数据可视化</a></li>
		</ul>
		<h4>Overlay interaction</h4>
		<ul>
			<li><a href="#edit-geometries">编辑几何图形</a></li>
			<li><a href="#time--elevation">时间 &amp; 海拔</a></li>
			<li><a href="#search--popups">搜索 &amp; 弹出框</a></li>
			<li><a href="#areaoverlay-selection">区域/覆盖选择</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>地图交互</h4>
		<ul>
			<li><a href="#layer-switching-controls">控制图层切换</a></li>
			<li><a href="#interactive-panzoom">交互式平移/缩放</a></li>
			<li><a href="#bookmarked-panzoom">带书签的平移/缩放</a></li>
			<li><a href="#fullscreen-controls">全屏</a></li>
			<li><a href="#minimaps--synced-maps">小地图 &amp; 同步地图</a></li>
			<li><a href="#measurement">测量</a></li>
			<li><a href="#mouse-coordinates">鼠标坐标</a></li>
			<li><a href="#events">事件</a></li>
			<li><a href="#user-interface">用户界面</a></li>
			<li><a href="#printexport">打印/导出</a></li>
			<li><a href="#geolocation">地理位置</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>各种各样的</h4>
		<ul>
			<li><a href="#geoprocessing">地理处理</a></li>
			<li><a href="#routing">路由</a></li>
			<li><a href="#geocoding">地理编码</a></li>
			<li><a href="#plugin-collections">插件集合</a></li>
		</ul>
		<h4>综合的</h4>
		<ul>
			<li><a href="#frameworks--build-systems">框架 &amp; 构建系统</a></li>
			<li><a href="#3rd-party-integration">3<sup>rd</sup> party</a></li>
		</ul>
		<hr>
		<a href="#develop-your-own">开发属于自己的插件</a>
	</div>
</div>

---

## Tile & image layers

下面的插件支持加载不同的地图并提供 Tile 和 Image 图层的功能。

* [Basemap providers](#basemap-providers)
* [Basemap formats](#basemap-formats)
* [Non-map base layers](#non-map-base-layers)
* [Tile/image display](#tileimage-display)
* [Tile load](#tile-load)
* [Vector tiles](#vector-tiles)


### Basemap providers

几乎不需要配置，开箱即用的底图。

{% include plugin_category_table.html category="basemap-providers" %}


### Basemap formats

以下插件用于加载常见格式（非默认）的底图或者栅格图层。

{% include plugin_category_table.html category="basemap-formats" %}

### Non-map base layers

有时候你不想加载地图，只想加载大的自定义图像，**非常大**的那种。

{% include plugin_category_table.html category="non-map-base-layers" %}

### Tile/image display

以下插件更改了地图中显示瓦片（tile）或图像(image)图层的方式。

{% include plugin_category_table.html category="tile-image-display" %}

### Tile Load

下面插件改变了将瓦片（Tile）图层加载到地图中的方式。

{% include plugin_category_table.html category="tile-load" %}

### Vector tiles

用来显示[矢量瓦片（Tile）](https://github.com/mapbox/vector-tile-spec) 的插件。

{% include plugin_category_table.html category="vector-tiles" %}


## Overlay data

以下插件提供了加载叠加数据（GIS 矢量数据）的新方法：点、线和多边形。

* [Overlay data formats](#overlay-data-formats)
* [Dynamic data loading](#dynamiccustom-data-loading)
* [Synthetic overlays](#synthetic-overlays)
* [Data providers](#data-providers)

### Overlay data formats

使用各种 GIS 格式加载你自己的数据。

{% include plugin_category_table.html category="overlay-data-formats" %}

### Dynamic/custom data loading

加载地图中更新的动态数据，或以非标准方式加载GIS矢量数据。

{% include plugin_category_table.html category="dynamic-custom-data-loading" %}

### Synthetic overlays

这些插件从头开始创建有用的叠加层，无需加载。

{% include plugin_category_table.html category="synthetic-overlays" %}

### Data providers

从三方服务加载 overlay 数据。 另请参阅 [Basemap providers](#basemap-providers) 和 [plugin collections](#collections).

{% include plugin_category_table.html category="data-providers" %}


## Overlay display

以下插件提供了显示 overlay 数据信息的新方法。

* [Markers & renderers](#markers--renderers)
* [Overlay animations](#overlay-animations)
* [Clustering/decluttering](#clusteringdecluttering)
* [Heatmaps](#heatmaps)
* [DataViz](#dataviz)


### Markers & renderers

这些插件提供了将抽象数据转换为屏幕中图像的新的标记（marker）或路径（way），精通 GIS 的 Leaflet 用户也将这些称为符号。

{% include plugin_category_table.html category="markers-renderers" %}

### Overlay animations

这些插件对标记物或一些几何图形进行动画处理。另请参阅[带时间或海拔的几何图形](#geometryinteraction-time)。

{% include plugin_category_table.html category="overlay-animations" %}

### Clustering/Decluttering

当您显示大量数据时，这些插件将使您的地图看起来更干净。

{% include plugin_category_table.html category="clustering-decluttering" %}

### Heatmaps

这些插件使用矢量数据创建可视化的热力图或类似热力图的图像。

{% include plugin_category_table.html category="heatmaps" %}

### DataViz

用于数据可视化的强大多用途库。

{% include plugin_category_table.html category="dataviz" %}


## Interaction with geometries/features

以下插件使用户能够与叠加数据互动：编辑几何图形，选择区域或特征，与时间维度互动，搜索特征并显示有关信息。

* [Edit geometries](#edit-geometries)
* [Time & elevation](#time--elevation)
* [Search & popups](#search--popups)
* [Area/overlay selection](#areaoverlay-selection)

### Edit geometries

允许用户创建、绘制、编辑和/或删除点、线和多边形。

{% include plugin_category_table.html category="edit-geometries" %}

### Time & elevation

大多数数据是二维的（经度和纬度），但有些数据有更多维度（高度和/或时间）。以下插件可以帮助用户浏览这些额外的维度。

{% include plugin_category_table.html category="time-elevation" %}

### Search & popups

搜索覆盖图层并增强如何显示有关覆盖图层的信息的插件。

{% include plugin_category_table.html category="search-popups" %}

### Area/overlay selection

这些插件帮助用户选择地图中的覆盖层或区域。

{% include plugin_category_table.html category="area-overlay-selection" %}


## Map interaction

与地图本身交互的新方法。

* [Layer switching controls](#layer-switching-controls)
* [Interactive pan/zoom](#interactive-panzoom)
* [Bookmarked pan/zoom](#bookmarked-panzoom)
* [Fullscreen](#fullscreen-controls)
* [Minimaps & synced maps](#minimaps--synced-maps)
* [Measurement](#measurement)
* [Mouse coordinates](#mouse-coordinates)
* [Events](#events)
* [User interface](#user-interface)
* [Print/export](#printexport)
* [Geolocation](#geolocation)

### Layer switching controls

以下插件用于增强或扩展 `L.Control.Layers`。

{% include plugin_category_table.html category="layer-switching-controls" %}


### Interactive pan/zoom

改变用户在地图上交互移动的方式。

{% include plugin_category_table.html category="interactive-pan-zoom" %}

### Bookmarked pan/zoom

通过跳转到预定义/存储的位置来改变用户在地图上移动的方式。

{% include plugin_category_table.html category="bookmarked-pan-zoom" %}

### Fullscreen controls

允许以全屏模式显示地图。

{% include plugin_category_table.html category="fullscreen-controls" %}

### Minimaps & synced maps

同时显示两张地图。其中一个可能是不同的尺寸和缩放级别，可作为最小地图使用，以帮助用户进行导航。

{% include plugin_category_table.html category="minimaps-synced-maps" %}

### Measurement

允许用户测量距离或面积。

{% include plugin_category_table.html category="measurement" %}

### Mouse coordinates

以不同方式显示鼠标光标下的地理坐标。

{% include plugin_category_table.html category="mouse-coordinates" %}

### Events

这些插件扩展了 Leaflet 的事件处理的能力。

{% include plugin_category_table.html category="events" %}

### User interface

按钮、滑块、工具栏、侧边栏和面板。

{% include plugin_category_table.html category="user-interface" %}

### Print/export

打印或导出你的地图。

<!--
- Saving a Leaflet Map to a PNG Example using Javascript and PHP https://github.com/tegansnyder/Leaflet-Save-Map-to-PNG
- Get a PNG from a Leaflet map and export it in PDF https://github.com/chrissom/leaflet-pdf
-->

{% include plugin_category_table.html category="print-export" %}

### Geolocation

扩展 Leaflet 地理定位功能的插件。

{% include plugin_category_table.html category="geolocation" %}


## Miscellaneous

### Geoprocessing

以下插件可进行多种地理信息处理（点、线和多边形上的数学和拓扑操作）。

{% include plugin_category_table.html category="geoprocessing" %}

### Routing

以下插件使用外部服务来计算驾驶或步行路线。

{% include plugin_category_table.html category="routing" %}

### Geocoding

将地址或地点名称转换为纬度和经度（反之亦然）的外部服务。

{% include plugin_category_table.html category="geocoding" %}

### Plugin collections

横跨几个类别的插件集。

插件开发人员：请将未来的插件保存在单独的存储库中。

{% include plugin_category_table.html category="plugin-collections" %}


## Integration

### Frameworks & build systems

将 Leaflet 集成到一个开发框架中，或为复杂的应用程序自动处理一些 javascript/CSS 工作，以简化你的开发工作。

{% include plugin_category_table.html category="frameworks-build-systems" %}

### 3<sup>rd</sup> party integration

以下插件将 Leaflet 集成到第三方服务或网站中。

{% include plugin_category_table.html category="3rd-party-integration" %}



## Develop your own

Leaflet 保持简单。如果你能想到一个并非所有 Leaflet 用户都需要的功能，并且你能以一种可重复使用的方式编写 JavaScript 代码，你就已经有了一个 Leaflet 插件。

对于如何创建自己的插件没有硬性要求，但我们鼓励所有的开发者阅读[插件指南](https://github.com/Leaflet/Leaflet/blob/master/PLUGIN-GUIDE.md)中的建议。

一旦您的插件准备就绪，您就可以将其提交到此列表：只需将添加到 [/docs/plugins.md](https://github.com/Leaflet/Leaflet/blob/master/docs/plugins.md) 的 PR 发送到我们的 GitHub 存储库。
