---
layout: post
title: Leaflet.MarkerCluster 0.1 发布
description: Leaflet.MarkerCluster，一个美观、快速、可定制的插件，用于减少拥挤地图上的视觉混乱
author: Dave Leaver
authorsite: https://github.com/danzel/
---

_这是一篇来自 Dave Leaver 的客座文章，他是一位活跃的 Leaflet 贡献者（特别是，他实现了 0.4 缩放动画的改进），也是目前最好的标记聚类插件的作者，在这篇文章中介绍了这个插件。_

几乎所有拥有一张带有标记的地图的人，最终都会出现这些标记重叠的情况。我在 <a href="http://www.smartrak.co.nz/" title="Smartrak GPS Fleet Tracking">Smartrak</a> 的日常工作中，我们经常有客户在地图上有成千上万的点。当你把它放大时，这些标记都会重叠，使地图看起来很乱很拥挤。还有一种情况是，即使在最大的缩放级别上，标记也会重叠，这就使得无法与它们进行互动。另外，在地图上有大量的标记，通常最终会将性能降低到一个不可接受的水平。

为了改善这一点，许多网站使用了标记聚类，这是一种将每个区段上彼此相近的标记分组的技术。这方面的一个好例子是 <a href="http://www.redfin.com/homes-for-sale">Redfin</a> 。我们需要类似的东西，但是在 Leaflet 中。本着开放源代码的精神，我们开发并发布了我们的解决方案，以便每个人都能利用它。因此，我们自豪地介绍 <a href="https://github.com/leaflet/Leaflet.markercluster">Leaflet.MarkerCluster</a> 。

<div id="map" class="map" style="height: 320px"></div>

{:#plugin-features}
### 特点

集群器有各种伟大的内置行为:

 * 一切都有出色的动画效果。当你放大和缩小时，你可以合乎逻辑地看到哪些集群变成了哪些标记。
 * 它的速度非常快，所以例如 [聚类 50000 点](https://leaflet.github.com/Leaflet.markercluster/example/marker-clustering-realworld.50000.html) 并不是问题。另外，所有繁重的计算都发生在最初的页面加载上，在这之后，地图就能顺利工作了。
 * 不需要聚类的标记是不需要的，而且在相关的缩放级别上也会看到。
 * 当你把鼠标放在一个群组上时，该群组内的标记的边界就会显示出来。
 * 点击一个群集将把你放大到它的子集的范围内。
 * 在底部的缩放级别，如果仍然有集群，你可以点击它们来 "spiderfy"，这使得与集群中的单个标记的互动成为可能（基于 <a href="https://github.com/jawj/OverlappingMarkerSpiderfier-Leaflet">jawj 的 Overlapping MarkerSpidifer</a> ）。
 * 为了提高性能，离视口超过一个屏幕宽度的集群和标记将从地图上删除。
 * 与核心 Leaflet 一样，所有东西都能在移动和桌面浏览器上运行，并一直测试到 IE6 。
 * 支持在被添加到地图后添加和删除标记（见下面的最佳做法！）。
 * 它是高度可定制的，允许你轻松改变集群的外观，禁用某些功能，并在集群互动上添加自定义行为。

### 使用方法

使用 Marker Clusterer 很简单，只要用 `L.MarkerClusterGroup` 替换你现有的 [LayerGroup](./././examples/layers-control.html) 用法即可：

    var markers = new L.MarkerClusterGroup();

	markers.addLayer(L.marker([175.3107, -37.7784]));
	// add more markers here...

	map.addLayer(markers);

你也可以对单个标记和集群使用所有的 [FeatureGroup 事件](.../.../reference.html#featuregroup) （另外还有 `clusterclick` ）。

	markers.on('clusterclick', function (a) { alert('Cluster Clicked'); });
	markers.on('click', function (a) { alert('Marker Clicked'); });

### 最佳实践

 * 为了从聚类器中获得最佳性能，你应该在将其添加到地图之前将所有的标记添加到聚类器中（就像我们在例子中做的那样）。
 * 如果你要移动一个在 L.MarkerClusterGroup 中的标记，你必须先移除它，然后移动它，再重新添加它。如果你在 MarkerClusterGroup 中移动它，我们就无法跟踪它，这个标记就会丢失。
 * 尽管聚类器支持在地图上添加和删除标记，但它的性能不如在不在地图上添加标记时好。如果你需要对一个 `MarkerClusterGroup`  中的标记进行大规模的更新，你可能想把它从地图上删除，改变标记，然后再重新添加它。

### 获取它

你可以在 <a href="https://github.com/leaflet/Leaflet.markercluster/downloads">github 下载页面</a> 上下载最新版本。

### 技术要点

底层聚类算法（ `MarkerClusterGroup._cluster` ）是普通的贪婪聚类。

{: .no-highlight}
    foreach marker
        如果在聚类距离内有一个聚类，就加入它。
        否则，如果在聚类距离内有一个未聚类的标记，就与它形成一个聚类。

第一个聚类步骤是针对最大（最底层）的缩放级别，然后我们对所有产生的标记和聚类进行聚类，生成下一个向上的缩放级别，以此类推，直到我们达到顶部。
这些集群被存储在一棵树上（一个集群包含它的子集群），具有良好的地理空间质量。我们使用这棵树来优化识别在任何特定缩放级别下屏幕上有哪些标记和集群。

#### L.DistanceGrid

`L.DistanceGrid` 在聚类时提供了一些不错的优化（由 [Vladimir](http://agafonkin.com/en/) 贡献，Leaflet 维护者）。

为了对标记进行聚类，我们需要将每个标记与其他每个标记进行比较，以尝试形成一个聚类。
为了使其更快，我们需要减少我们需要比较的标记的集合。`DistanceGrid` 通过将所有标记放在一个大小与我们需要搜索的距离相同的网格上来实现。然后，当我们寻找一个要聚类的标记时，我们只需要看我们所在的网格方块和它的近邻的标记。这可能是一个相当大的性能优势，因为我们只看我们有可能形成集群的标记。( <a href="https://github.com/leaflet/Leaflet.markercluster/pull/29">查看数字的初始 PR</a> )

### 结语

我希望你喜欢使用聚类器，并从中获得你想要的一切。如果你在公共网站上使用它，请  <a href="mailto:danzel@localhost.geek.nz">给我发一封邮件</a>  ，这样我可以检查一下，并有可能将其链接到 github 网站上。

如果你有任何问题，也请在 <a href="https://github.com/leaflet/Leaflet.markercluster">github 页面</a> 上记录一个错误。

Enjoy!<br />
Dave Leaver.

<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.markercluster/dist/MarkerCluster.css" />
<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.markercluster/dist/MarkerCluster.Default.css" />
<!--[if lte IE 8]><link rel="stylesheet" href="https://leaflet.github.io/Leaflet.markercluster/dist/MarkerCluster.Default.ie.css" /><![endif]-->
<script src="https://leaflet.github.io/Leaflet.markercluster/dist/leaflet.markercluster-src.js"></script>
<script src="https://leaflet.github.io/Leaflet.markercluster/example/realworld.388.js"></script>

<script>
	var mapbox = new L.TileLayer(MB_URL, {maxZoom: 18, attribution: MB_ATTR, id: 'examples.map-i875mjb7'}),
		latlng = new L.LatLng(-37.820, 175.217);

	var map = new L.Map('map', {center: latlng, zoom: 15, layers: [mapbox]});

	map.attributionControl.addAttribution("Points &copy 2012 LINZ");

	var markers = new L.MarkerClusterGroup();

	for (var i = 0; i < addressPoints.length; i++) {
		var a = addressPoints[i];
		var title = a[2];
		var marker = new L.Marker(new L.LatLng(a[0], a[1]), { title: title });
		marker.bindPopup(title);
		markers.addLayer(marker);
	}

	map.addLayer(markers);
</script>
