---
layout: post
title: Leaflet.draw 0.2 发布
description: Leaflet.draw 0.2 正式发布 —— 为您的 Leaflet 地图带来矢量绘图和编辑工具
author: Jacob Toye
authorsite: https://github.com/jacobtoye/
---

这是 Jacob Toye的客座文章，他是 Leaflet 的活跃贡献者，同时也是目前最复杂的矢量绘图和编辑插件的作者，在这篇文章中介绍了这个插件。

[Leaflet.draw](https://github.com/Leaflet/Leaflet.draw/) 诞生于为用户提供在地图上绘制多边形的能力的需要。Leaflet 已经提供了一个非常好的方法来编辑现有的折线和多边形。合乎逻辑的下一步是在这个功能上进行扩展，以允许创建这些图层，并最终创建其他的矢量图层。

一经发布，Leaflet 社区的直接反应是非常积极的。很明显，下一步将是把这个工具发展到用户除了创建形状之外还可以编辑和删除形状的状态。这就是 Leaflet.draw 0.2 最终要做的事情。

经过几个月的断断续续的开发，在我的雇主 <a href="http://www.smartrak.co.nz" title="GPS车队管理解决方案" target="_blank">Smartrak</a> 的赞助下，我们隆重推出 Leaflet.draw 0.2 ———— 你在 Leaflet 地图上绘制、编辑和删除矢量和标记的一站式插件。:) 

来自 Vladimir 的注意：Leaflet 核心的多线、多边形编辑功能已经被移到这个插件中，在那里它更适合。该插件又被移到了 [GitHub 上的 Leaflet 组织](https://github.com/Leaflet) ，现在已被 Leaflet 开发团队正式支持。请注意，0.2 版目前依赖于 Leaflet master（正在开发的版本）来工作。

您可以从 <a href="https://github.com/Leaflet/Leaflet.draw/" target="_blank" >github repo</a> 下载最新版本。请在 <a href="https://github.com/Leaflet/Leaflet.draw/issues" target="_blank" >问题页面</a> 上报告您遇到的任何错误。

<div id="map" class="map" style="height: 288px"></div>

{:#plugin-features}
### 特点

Leaflet.draw 的设计不仅便于终端用户使用，而且也便于开发者整合。

 * 用易于使用的绘图工具在地图上绘制形状。
 * 编辑和删除矢量和标记。
 * 超级可定制:
   * 自定义每个形状的风格，以适应你的地图主题。
   * 挑选你想使用的工具。
   * 只需使用绘图和编辑处理程序，就可以推出你自己的。
 * 基于事件的系统允许你在形状被创建、编辑或删除时执行任何必要的行动。

### 如何使用

Leaflet.draw 非常简单，可以放入你的 Leaflet 应用程序中。下面的例子将在一张地图上添加绘图和编辑工具栏:

	// 在 "map"栏目中创建一个地图，将视图设置为指定地点并进行缩放。
	var map = L.map('map').setView([175.30867, -37.77914], 13);

	// 添加一个OpenStreetMap 的瓦片层
	L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
		attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
	}).addTo(map);

	// 初始化FeatureGroup来存储可编辑的图层
	var drawnItems = new L.FeatureGroup();
	map.addLayer(drawnItems);

	// 初始化绘图控件，并将可编辑层的特征组传递给它
	var drawControl = new L.Control.Draw({
		edit: {
			featureGroup: drawnItems
		}
	});
	map.addControl(drawControl);

#### 处理新创建的图层

一旦你成功地将 Leaflet.draw 插件添加到你的地图中，你就会想对用户可能触发的不同动作做出反应。

	map.on('draw:created', function (e) {
		var type = e.layerType,
			layer = e.layer;

		if (type === 'marker') {
			// 做标记的具体行动
		}

		// 做其他你需要做的事情。(保存到数据库，添加到地图等)
		drawnItems.addLayer(layer);
	});

	map.on('draw:edited', function () {
		// 更新数据库以保存最新的变化。
	});

	map.on('draw:deleted', function () {
		// 更新数据库以保存最新的变化。
	});

请参阅 <a href="https://github.com/Leaflet/Leaflet.draw" target="_blank">Leaflet.draw README</a> 以了解关于如何配置该插件的更多细节。

### 谢谢

首先，我想感谢我的雇主 <a href="http://www.smartrak.co.nz" title="GPS车队管理解决方案" target="_blank">Smartrak</a> 。如果没有他们对开源软件的态度，我就不会有时间来完成这个插件。

Leaflet 开发者社区通过灵感、拉动请求和问题报告对这个插件给予了极大的支持。特别感谢。 <a href="https://github.com/mourner" title="@mourner" target="_blank" >@mourner</a> 、 <a href="https://github.com/danzel" title="@danzel" target="_blank" >@danzel</a> 、 <a href="https://github.com/brunob" title="@brunob" target="_blank" >@brunob</a> 、 <a href="https://github. com/tnightingale" title="@tnightingale" target="_blank" >@tnightingale</a> 、 <a href="https://github.com/Starefossen" title="@Starefossen" target="_blank" >@Starefossen</a>  和 <a href="https://github.com/shramov" title="@shramov" target="_blank" >@shramov</a> 。

### 关闭

我在实施这个插件时很开心。我希望你喜欢使用它。如果您有问题或只是想问候一下，请给我发电子邮件： <a href="mailto:jacob.toye@gmail.com">jacob.toye@gmail.com</a> 。

Cheers,
Jacob Toye

<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.draw/lib/leaflet/leaflet.css" />
<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.draw/leaflet.draw.css" />
<!--[if lte IE 8]>
	<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.draw/lib/leaflet/leaflet.ie.css" />
	<link rel="stylesheet" href="https://leaflet.github.io/Leaflet.draw/leaflet.draw.ie.css" />
<![endif]-->
<script src="https://leaflet.github.io/Leaflet.draw/libs/leaflet/leaflet.js"></script>
<script src="https://leaflet.github.io/Leaflet.draw/leaflet.draw.js"></script>

<style>
	.leaflet-bar {
		border: none;
	}
</style>

<script>
	// create a map in the "map" div, set the view to a given place and zoom
	var map = L.map('map').setView([-37.77914, 175.30867], 16);

	// add an OpenStreetMap tile layer
	L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
	  attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
	}).addTo(map);

	// Initialize the FeatureGroup to store editable layers
	var drawnItems = new L.FeatureGroup();
	map.addLayer(drawnItems);

	// Initialize the draw control and pass it the FeatureGroup of editable layers
	var drawControl = new L.Control.Draw({
		edit: {
			featureGroup: drawnItems
		}
	});
	map.addControl(drawControl);

	map.on('draw:created', function (e) {
		var type = e.layerType,
			layer = e.layer;

		if (type === 'marker') {
			layer.bindPopup('A popup!');
		}

		// Do whatever else you need to. (save to db, add to map etc)
		drawnItems.addLayer(layer);
	});
</script>
