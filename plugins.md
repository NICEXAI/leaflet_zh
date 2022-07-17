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

The following plugins allow loading different maps and provide functionality to tile and image layers.

* [Basemap providers](#basemap-providers)
* [Basemap formats](#basemap-formats)
* [Non-map base layers](#non-map-base-layers)
* [Tile/image display](#tileimage-display)
* [Tile load](#tile-load)
* [Vector tiles](#vector-tiles)


### Basemap providers

Ready-to-go basemaps, with little or no configuration at all.

{% include plugin_category_table.html category="basemap-providers" %}


### Basemap formats

Plugins for loading basemaps or GIS raster layers in common (albeit non-default) formats.

{% include plugin_category_table.html category="basemap-formats" %}

### Non-map base layers

Sometimes you don't want to load a map, just big custom images. **Really** big ones.

{% include plugin_category_table.html category="non-map-base-layers" %}

### Tile/image display

The following plugins change the way that tile or image layers are displayed in the map.

{% include plugin_category_table.html category="tile-image-display" %}

### Tile Load

The following plugins change the way that tile layers are loaded into the map.

{% include plugin_category_table.html category="tile-load" %}

### Vector tiles

Plugins to display [vector tiles](https://github.com/mapbox/vector-tile-spec).

{% include plugin_category_table.html category="vector-tiles" %}


## Overlay data

The following plugins provide new ways of loading overlay data (GIS vector data): points, lines and polygons.

* [Overlay data formats](#overlay-data-formats)
* [Dynamic data loading](#dynamiccustom-data-loading)
* [Synthetic overlays](#synthetic-overlays)
* [Data providers](#data-providers)

### Overlay data formats

Load your own data from various GIS formats.

{% include plugin_category_table.html category="overlay-data-formats" %}

### Dynamic/custom data loading

Load dynamic data which is updated in the map, or load GIS vector data in non-standard ways.

{% include plugin_category_table.html category="dynamic-custom-data-loading" %}

### Synthetic overlays

These plugins create useful overlays from scratch, no loading required.

{% include plugin_category_table.html category="synthetic-overlays" %}

### Data providers

Load overlay data from third-party-services. See also [basemap providers](#basemap-providers) and [plugin collections](#collections).

{% include plugin_category_table.html category="data-providers" %}


## Overlay display

The following plugins provide new ways of displaying overlay data information.

* [Markers & renderers](#markers--renderers)
* [Overlay animations](#overlay-animations)
* [Clustering/decluttering](#clusteringdecluttering)
* [Heatmaps](#heatmaps)
* [DataViz](#dataviz)


### Markers & renderers

These plugins provide new markers or news ways of converting abstract data into images in your screen. Leaflet users versed in GIS also know these as symbolizers.

{% include plugin_category_table.html category="markers-renderers" %}

### Overlay animations

These plugins animate markers or some geometries. See also [geometries with time or elevation](#geometryinteraction-time).

{% include plugin_category_table.html category="overlay-animations" %}

### Clustering/Decluttering

When you are displaying a lot of data, these plugins will make your map look cleaner.

{% include plugin_category_table.html category="clustering-decluttering" %}

### Heatmaps

These plugins create heatmaps and heatmap-like visualizations from vector data.

{% include plugin_category_table.html category="heatmaps" %}

### DataViz

Powerful multi-purpose libraries for data visualization.

{% include plugin_category_table.html category="dataviz" %}


## Interaction with geometries/features

The following plugins enable users to interact with overlay data: edit geometries, select areas or features, interact with the time dimension, search features and display information about them.

* [Edit geometries](#edit-geometries)
* [Time & elevation](#time--elevation)
* [Search & popups](#search--popups)
* [Area/overlay selection](#areaoverlay-selection)

### Edit geometries

Allows users to create, draw, edit and/or delete points, lines and polygons.

{% include plugin_category_table.html category="edit-geometries" %}

### Time & elevation

Most data is two-dimensional (latitude and longitude), but some data has more dimensions (altitude and/or time). The following plugins help users navigate these extra dimensions.

{% include plugin_category_table.html category="time-elevation" %}

### Search & popups

Plugins that search for overlays and enhance how to display information about them.

{% include plugin_category_table.html category="search-popups" %}

### Area/overlay selection

These plugins help users select either overlays or areas in the map.

{% include plugin_category_table.html category="area-overlay-selection" %}


## Map interaction

New ways to interact with the map itself.

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

The following plugins enhance or extend `L.Control.Layers`.

{% include plugin_category_table.html category="layer-switching-controls" %}


### Interactive pan/zoom

Change the way the user can interactively move around the map.

{% include plugin_category_table.html category="interactive-pan-zoom" %}

### Bookmarked pan/zoom

Change the way the user is moved around the map, by jumping to predefined/stored places.

{% include plugin_category_table.html category="bookmarked-pan-zoom" %}

### Fullscreen controls

Allows display of the map in full-screen mode.

{% include plugin_category_table.html category="fullscreen-controls" %}

### Minimaps & synced maps

Display two maps at once. One of them might be a different size and zoom level, usable as a minimap to aid with navigation.

{% include plugin_category_table.html category="minimaps-synced-maps" %}

### Measurement

Allow the user to measure distances or areas.

{% include plugin_category_table.html category="measurement" %}

### Mouse coordinates

Show the geographical coordinates under the mouse cursor in different ways.

{% include plugin_category_table.html category="mouse-coordinates" %}

### Events

These plugins extend Leaflet event handling.

{% include plugin_category_table.html category="events" %}

### User interface

Buttons, sliders, toolbars, sidebars, and panels.

{% include plugin_category_table.html category="user-interface" %}

### Print/export

Print or export your map.

<!--
- Saving a Leaflet Map to a PNG Example using Javascript and PHP https://github.com/tegansnyder/Leaflet-Save-Map-to-PNG
- Get a PNG from a Leaflet map and export it in PDF https://github.com/chrissom/leaflet-pdf
-->

{% include plugin_category_table.html category="print-export" %}

### Geolocation

Plugins that extend Leaflet's geolocation capabilities.

{% include plugin_category_table.html category="geolocation" %}


## Miscellaneous

### Geoprocessing

The following plugins perform several sorts of geoprocessing (mathematical and topological operations on points, lines and polygons).

{% include plugin_category_table.html category="geoprocessing" %}

### Routing

The following plugins use external services to calculate driving or walking routes.

{% include plugin_category_table.html category="routing" %}

### Geocoding

External services that transform an address or the name of a place into latitude and longitude (or vice versa).

{% include plugin_category_table.html category="geocoding" %}

### Plugin collections

Sets of plugins that span several categories.

Plugin developers: please keep future plugins in individual repositories.

{% include plugin_category_table.html category="plugin-collections" %}


## Integration

### Frameworks & build systems

Ease your development integrating Leaflet into a development framework or automating some of the javascript/CSS work for complex applications.

{% include plugin_category_table.html category="frameworks-build-systems" %}

### 3<sup>rd</sup> party integration

The following plugins integrate Leaflet into third party services or websites.

{% include plugin_category_table.html category="3rd-party-integration" %}



## Develop your own

Leaflet keeps it simple. If you can think of a feature that is not required by all Leaflet users, and you can write the JavaScript code in a reusable way, you've got yourself a Leaflet plugin already.

There are no hard requirements on how to create your own plugin, but all developers are encouraged to read the recommendations in the [plugin guide](https://github.com/Leaflet/Leaflet/blob/main/PLUGIN-GUIDE.md).

Once your plugin is ready, you can submit it: just send a pull request with a new plugin file in [/docs/_plugins/](https://github.com/Leaflet/Leaflet/tree/main/docs/_plugins)to our GitHub repository.
