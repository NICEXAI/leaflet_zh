---
layout: post
title: Leaflet 0.4.3 和 新的教程
description: Leaflet 0.4.3 发布了几个错误修正和改进，并附带了一个关于创建彩色交互式等值线地图的新教程
author: Vladimir Agafonkin
authorsite: http://agafonkin.com/en
---

继 [Leaflet 0.4 发布](leaflet-0-4-released.html) 之后，在过去的一周里有几个小的 bug 修复版本，Leaflet 0.4.3 今天发布。它们包含了对一些被发现的 bug 的修复，同时也为新的 GeoJSON API 带来了一些改进，使其更加灵活——————见下面的更新日志。

我还写了 [一个新的教程](./././examples/choropleth.html) ，灵感来自 [Ryan Murphy](http://www.texastribune.org/about/staff/ryan-murphy/) 的[Texas Tribune US Senate Runoff Results map](http://www.texastribune.org/library/data/us-senate-runoff-results-map/)（也是由 Leaflet 驱动的）。它将逐步向你展示如何在 GeoJSON 和自定义控件的帮助下创建一个漂亮的美国各州人口密度互动 [choropleth 地图](http://en.wikipedia.org/wiki/Choropleth_map) ，并希望能说服更多的主要新闻和政府网站转向使用 Leaflet 。

在 [下载页面](../../../download.html) 获取新的 Leaflet 0.4.3 。享受吧!

**更新**。在 0.4.3 中发现了 IE9 的兼容问题，所以我不得不发布 0.4.4 ，并进行了修复。对此表示非常抱歉。

### 0.4.3 (2012年8月7日)

#### 改进措施

 * 改进了 `GeoJSON` `setStyle` ，使其也能接受函数（如相应的选项）。
 * 增加了 `GeoJSON` `resetStyle(layer)` ，对重设悬停状态很有用。
 * 为用 `GeoJSON` 创建的图层（包含 GeoJSON 特征数据）增加了 `feature` 属性。
 * 增加了 `FeatureGroup` `bringToFront` 和 `bringToBack` 方法（以便它们能适用于多聚体）。
 * 为 `Map` `invalidateSize` 增加了可选的 `animate` 参数(由 [@ajbeaven](https://github.com/ajbeaven) )。 [#857](https://github.com/Leaflet/Leaflet/pull/857)

#### 错误修复

 * 修正了在安卓 2、3 系统上初始加载地图时瓷砖有时会消失的问题（由 [@danzel](https://github.com/danzel) 提供）。 [#868](https://github.com/Leaflet/Leaflet/pull/868)
 * 修正了一个错误，即在 Chrome 浏览器上放大或平移时，地图在边界附近偶尔会闪烁。
 * 修正了一个错误，即 `Path` `bringToFront` 和 `bringToBack` 没有返回 `this` 。
 * 删除了 Win、Meta 键绑定的放大功能（因为它干扰了全局键盘快捷键）。 [#869](https://github.com/Leaflet/Leaflet/issues/869)

### 0.4.2 (2012年8月1日)

 * 修正了层控制单选按钮在 IE7 中不能正常工作的问题（由 [@danzel](https://github.com/danzel) ）。 [#862](https://github.com/Leaflet/Leaflet/pull/862)
 * 修正了一个错误，即 `FeatureGroup` `removeLayer` 会解除对已删除图层的弹出窗口的绑定，即使这些弹出窗口不是由该组放置的(影响到 [Leaflet.markercluster](https://github.com/danzel/Leaflet.markercluster) 插件)(由 [@danzel](https://github.com/danzel) )。 [#861](https://github.com/Leaflet/Leaflet/pull/861)

### 0.4.1 (2012年7月31日)

 * 修正了一个在 IE6-8 中导致标记阴影显示为不透明黑色的错误。 [#850](https://github.com/Leaflet/Leaflet/issues/850)
 * 修正了一个错误，即比例控制对比例的计算不正确。 [#852](https://github.com/Leaflet/Leaflet/issues/852)
 * 修正了破损的 L.tileLayer.wms 类工厂（由 [@mattcurrie](https://github.com/mattcurrie) ）。 [#856](https://github.com/Leaflet/Leaflet/issues/856)
 * 改进了 `TileLayer` `detectRetina` 选项的视网膜检测（由 [@sxua](https://github.com/sxua) ）。 [#854](https://github.com/Leaflet/Leaflet/issues/854)

Sincerely, <br />
Vladimir Agafonkin, Leaflet maintainer.
