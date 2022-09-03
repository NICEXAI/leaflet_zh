---
layout: tutorial_v2
title: Working with map panes
---

## 什么是 pane ?

在 Leaflet 中，map panes 隐式地将图层组合在一起，而开发者并不知道这一点。这种分组允许 Web 浏览器以比单独处理图层更有效的方式同时处理多个图层。

Map panes 使用 z-index CSS 属性来让某些图层始终显示在其他图层之上。[默认的排序](/reference.html#map-pane)是：

* `TileLayer` 和 `GridLayer`
* `Path`, 如线、折线、圆或 `GeoJSON` 图层
* `Marker` 阴影
* `Marker` 图标
* `Popup`

这就是为什么在 Leaflet 地图中，popups 总是显示在其他层的 "上面"，markers 总是显示在瓦片图层的上面，等等。

**Leaflet 1.0.0** 的一个新功能（0.7.x 中没有）是自定义 map panes，它允许自定义这个顺序。

## 默认情况并不总是正确的

在某些特定情况下，默认顺序不是地图的正确顺序。我们可以用 [Carto basemaps](https://carto.com/location-data-services/basemaps/) 底图和标签来证明这一点：


<style>
.tiles img {
    border: 1px solid #ccc;
    border-radius: 5px;
}
</style>

<div class='tiles'>
<div style='display: inline-block'>
<img src="https://a.basemaps.cartocdn.com/light_nolabels/4/8/5.png" class="bordered-img" /><br/>
没有标签的底图
</div>

<div style='display: inline-block'>
<img src="https://a.basemaps.cartocdn.com/light_only_labels/4/8/5.png" class="bordered-img" /><br/>
仅有透明标签的瓦片图层
</div>

<div style='display: inline-block; position:relative;'>
<img src="https://a.basemaps.cartocdn.com/light_nolabels/4/8/5.png" class="bordered-img" />
<img src="https://a.basemaps.cartocdn.com/light_only_labels/4/8/5.png"  style='position:absolute; left:0; top:0;'/><br/>
底图顶部的标签
</div>
</div>

如果我们用这两个图层创建一个 Leaflet 地图，任何标记或多边形都会显示在这两个图层的上面，但是把标签放在上面[看起来更好](http://blog.cartodb.com/let-your-labels-shine/)，我们怎样才能做到这一点呢？

{% include frame.html url="example.html" %}

## 自定义 pane

我们可以使用默认的底图瓦片（tile）和一些像 GeoJSON 图层这样的覆盖物, 然后我们必须为标签定义一个自定义窗格（pane），以便它们显示在 GeoJSON 数据之上。

自定义 map panes 是在每个地图的基础上创建的，所以首先创建一个 `L.Map` 的实例和 pane:


    var map = L.map('map');
    map.createPane('labels');


下一步是设置窗格的z-index。查看[默认值](https://github.com/Leaflet/Leaflet/blob/v1.0.0/dist/leaflet.css#L87)为650，这将使带有标签的 `TileLayer` 显示在标记的上面和弹窗窗口的下面。通过使用 `getPane()`，我们获得了对 [`HTMLElement`](https://developer.mozilla.org/docs/Web/API/HTMLElement) 表示窗格的引用，并更改它的 z-index：


    map.getPane('labels').style.zIndex = 650;


在其他地图层之上设置图像标签的一个问题是，这些标签会捕捉到点击和触摸事件。如果用户点击地图上的任何地方，网络浏览器会认为她点击的是标签瓦片，而不是 GeoJSON 或标记物。这个问题可以用 [`pointer-events` CSS 属性](https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events)来解决：


    map.getPane('labels').style.pointerEvents = 'none';


窗格（pane）准备就绪后，我们可以添加图层，注意使用标签瓦片（tile）上的 `pane` 选项：


    var positron = L.tileLayer('https://{s}.basemaps.cartocdn.com/light_nolabels/{z}/{x}/{y}.png', {
            attribution: '©OpenStreetMap, ©CartoDB'
    }).addTo(map);

    var positronLabels = L.tileLayer('https://{s}.basemaps.cartocdn.com/light_only_labels/{z}/{x}/{y}.png', {
            attribution: '©OpenStreetMap, ©CartoDB',
            pane: 'labels'
    }).addTo(map);

    var geojson = L.geoJson(GeoJsonData, geoJsonOptions).addTo(map);

最后，为 GeoJSON 层上的每个 feature 添加一些交互：

    geojson.eachLayer(function (layer) {
        layer.bindPopup(layer.feature.properties.name);
    });

    map.fitBounds(geojson.getBounds());


现在，[示例地图](example.html)已经完成了!



