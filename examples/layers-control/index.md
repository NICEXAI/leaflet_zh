---
layout: tutorial_v2
title: Layer Groups and Layers Control
---

## Layer Groups 和 Layers Control

本教程将告诉你如何将几个图层组合成一个，以及如何使用图层控件让用户在你的地图上轻松切换不同的图层。

{% include frame.html url="example.html" %}

### Layer Groups

假设您想将一堆图层合并到一个分组中，以便在代码中将它们作为一个处理：

	var littleton = L.marker([39.61, -105.02]).bindPopup('This is Littleton, CO.'),
		denver    = L.marker([39.74, -104.99]).bindPopup('This is Denver, CO.'),
		aurora    = L.marker([39.73, -104.8]).bindPopup('This is Aurora, CO.'),
	    golden    = L.marker([39.77, -105.23]).bindPopup('This is Golden, CO.');

您可以使用 <a href="/reference.html#layergroup">LayerGroup</a> 类执行以下操作，而不是直接将它们添加到地图中：

	var cities = L.layerGroup([littleton, denver, aurora, golden]);

足够简单! 现在你有了一个 "cities" 图层，它将你的城市标记合并成一个图层，你可以一次性地从地图上添加或删除。

### Layers Control

Leaflet有一个很好的小控件，允许你的用户控制他们在你的地图上看到哪些图层。除了向你展示如何使用它之外，我们还将向你展示图层组的另一个方便的用途。

有两种类型的图层。(1)互斥的基础图层（一次只能有一个在地图上可见），例如瓦片图层，和(2)覆盖层，即你放在基础图层上的所有其他东西。在这个例子中，我们希望有两个基础图层（一个灰度图层和一个彩色基础图层）可以切换，还有一个覆盖层可以开关：我们之前创建的城市标记。

现在让我们创建这些基础图层并将默认图层添加到地图中：

<pre><code>var grayscale = L.tileLayer(mapboxUrl, {id: '<a href="https://mapbox.com">MapID</a>', tileSize: 512, zoomOffset: -1, attribution: mapboxAttribution}),
	streets   = L.tileLayer(mapboxUrl, {id: '<a href="https://mapbox.com">MapID</a>', tileSize: 512, zoomOffset: -1, attribution: mapboxAttribution});

var map = L.map('map', {
	center: [39.73, -104.99],
	zoom: 10,
	layers: [grayscale, cities]
});</code></pre>

接下来，我们将创建两个对象。一个包含我们的基础层，另一个将包含我们的覆盖层。这些只是带有键/值对的简单对象。键设置控件中图层的文本（例如`streets`），而相应的值是对图层的引用（例如streets）。

<pre><code>var baseMaps = {
	"Grayscale": grayscale,
	"Streets": streets
};

var overlayMaps = {
    "Cities": cities
};</code></pre>

现在，剩下的就是创建一个[图层控件](/reference.html#control-layers)并将其添加到地图中。创建图层控制时传递的第一个参数是基本图层对象。第二个参数是覆盖层对象。两个参数都是可选的：你可以通过省略第二个参数来传递一个基本图层对象，或者通过传递`null'作为第一个参数来传递一个覆盖对象。在每种情况下，省略的图层类型将不会出现供用户选择。

<pre><code>L.control.layers(baseMaps, overlayMaps).addTo(map);</code></pre>

注意，我们在地图上添加了 `grayscale` 和 `cities` 层，但没有添加 `streets`。图层控件很聪明，可以检测出我们已经添加了哪些图层，并设置了相应的复选框和辐射框。

还要注意的是，当使用多个基础图层时，在实例化时只应将其中一个图层添加到地图中，但在创建图层控件时，所有的图层都应存在于基础图层对象中。

最后，您可以在为图层定义对象时设置关键帧的样式。例如，此代码将使灰度图的标签变灰：

<pre><code>var baseMaps = {
	"&lt;span style='color: gray'&gt;Grayscale&lt;/span&gt;": grayscale,
	"Streets": streets
};
</code></pre>

现在让我们在[单独的页面上查看最终效果&rarr;](example.html)。

