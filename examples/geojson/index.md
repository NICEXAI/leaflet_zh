---
layout: tutorial_v2
title: Using GeoJSON with Leaflet
---

<h3>在 Leaflet 中使用 GeoJSON</h3>

<p>GeoJSON 正在成为许多 GIS 技术和服务中非常流行的数据格式--它简单、轻量、直接，而且 Leaflet 在处理 GeoJSON 方面也相当出色。在本教程中，你将学习如何创建并与由 <a href="https://tools.ietf.org/html/rfc7946">GeoJSON</a> 对象创建的矢量地图进行交互。</p>

{% include frame.html url="example.html" %}

<h3>关于 GeoJSON</h3>

<p>根据 <a href="https://tools.ietf.org/html/rfc7946">GeoJSON 规范（RFC 7946）</a>：</p>

<blockquote>GeoJSON 是一种用于编码各种地理数据结构的格式[...]。一个 GeoJSON 对象可以代表一个空间区域（Geometry），一个有空间界限的实体（Feature），或者一个特征列表（FeatureCollection）。GeoJSON支持以下几何体类型。点、线字符串、多边形、多点、多线字符串、多多边形和几何体集合。GeoJSON 中的特征包含一个几何对象和额外的属性，而特征集合则包含一个特征列表。</blockquote>

<p>Leaflet 支持上述所有的 GeoJSON 类型，但是 <a href="https://tools.ietf.org/html/rfc7946#section-3.2">Features</a> 和 <a href="https://tools.ietf.org/html/rfc7946#section-3.3">FeatureCollections</a> 效果最好，因为它们允许你用一组属性来描述特征。我们甚至可以使用这些属性来为我们的 Leaflet 向量设置样式。下面是一个简单的 GeoJSON feature 的例子：</p>

<pre><code>var geojsonFeature = {
	"type": "Feature",
	"properties": {
		"name": "Coors Field",
		"amenity": "Baseball Stadium",
		"popupContent": "This is where the Rockies play!"
	},
	"geometry": {
		"type": "Point",
		"coordinates": [-104.99404, 39.75621]
	}
};
</code></pre>

<h3>GeoJSON 图层</h3>

<p>GeoJSON 对象是通过 <a href="/reference.html#geojson">GeoJSON 图层</a>添加到地图上的。要创建它并将其添加到地图上，我们可以使用以下代码：</p>

<pre><code>L.geoJSON(geojsonFeature).addTo(map);</code></pre>

<p>GeoJSON 对象也可以作为一个有效的 GeoJSON 对象的数组来传递。</p>

<pre><code>var myLines = [{
	"type": "LineString",
	"coordinates": [[-100, 40], [-105, 45], [-110, 55]]
}, {
	"type": "LineString",
	"coordinates": [[-105, 40], [-110, 45], [-115, 55]]
}];
</code></pre>

<p>另外，我们可以创建一个空的 GeoJSON 图层，并将其分配给一个变量，这样我们就可以在以后向其添加更多的特征。</p>

<pre><code>var myLayer = L.geoJSON().addTo(map);
myLayer.addData(geojsonFeature);
</code></pre>

<h3>选项</h3>

<h4>style</h4>

<p><code>style</code>选项可用于以两种不同的方式为特征设置样式。首先，我们可以传入一个简单的对象，以相同的方式对所有路径（折线和多边形）进行样式处理：</p>

<pre><code>var myLines = [{
	"type": "LineString",
	"coordinates": [[-100, 40], [-105, 45], [-110, 55]]
}, {
	"type": "LineString",
	"coordinates": [[-105, 40], [-110, 45], [-115, 55]]
}];

var myStyle = {
	"color": "#ff7800",
	"weight": 5,
	"opacity": 0.65
};

L.geoJSON(myLines, {
	style: myStyle
}).addTo(map);</code></pre>

<p>另外，我们也可以传递一个函数，根据单个特征的属性来确定其样式。在下面的例子中，我们检查了 "party "属性，并相应地设计了我们的多边形：</p>

<pre><code>var states = [{
	"type": "Feature",
	"properties": {"party": "Republican"},
	"geometry": {
		"type": "Polygon",
		"coordinates": [[
			[-104.05, 48.99],
			[-97.22,  48.98],
			[-96.58,  45.94],
			[-104.03, 45.94],
			[-104.05, 48.99]
		]]
	}
}, {
	"type": "Feature",
	"properties": {"party": "Democrat"},
	"geometry": {
		"type": "Polygon",
		"coordinates": [[
			[-109.05, 41.00],
			[-102.06, 40.99],
			[-102.03, 36.99],
			[-109.04, 36.99],
			[-109.05, 41.00]
		]]
	}
}];

L.geoJSON(states, {
	style: function(feature) {
		switch (feature.properties.party) {
			case 'Republican': return {color: "#ff0000"};
			case 'Democrat':   return {color: "#0000ff"};
		}
	}
}).addTo(map);</code></pre>

<h4>pointToLayer</h4>

<p>点的处理方式与多线和多边形不同。默认情况下，GeoJSON 点会画出简单的标记。我们可以通过在创建 GeoJSON 图层时在 <a href="/reference.html#geojson">GeoJSON 选项</a>对象中传递一个 <code>pointToLayer</code> 函数来改变这一点。这个函数会传递一个 <a href="/reference.html#latlng">LatLng</a>，并且应该返回一个 ILayer 的实例，在这种情况下可能是 <a href="/reference.html#marker">Marker</a> 或者 <a href="/reference.html#circlemarker">CircleMarker</a>。</p>

<p>这里我们使用 <code>pointToLayer</code> 选项来创建一个 CircleMarker：</p>

<pre><code>var geojsonMarkerOptions = {
	radius: 8,
	fillColor: "#ff7800",
	color: "#000",
	weight: 1,
	opacity: 1,
	fillOpacity: 0.8
};

L.geoJSON(someGeojsonFeature, {
	pointToLayer: function (feature, latlng) {
		return L.circleMarker(latlng, geojsonMarkerOptions);
	}
}).addTo(map);</code></pre>

<p>我们也可以在这个例子中设置 <code>style</code> 属性&mdash; 如果你在 <code>pointToLayer</code> 函数里面创建了一个像圆一样的矢量层，Leaflet 会很聪明地将样式应用到 GeoJSON Point。</p>

<h4>onEachFeature</h4>

<p><code>onEachFeature</code> 选项是一个函数，在将其添加到 GeoJSON 图层之前，会对每个 Feature 进行调用。使用这个选项的一个常见原因是在点击地物的时候给它们附加一个弹出窗口。</p>

<pre><code>function onEachFeature(feature, layer) {
	// does this feature have a property named popupContent?
	if (feature.properties &amp;&amp; feature.properties.popupContent) {
		layer.bindPopup(feature.properties.popupContent);
	}
}

var geojsonFeature = {
	"type": "Feature",
	"properties": {
		"name": "Coors Field",
		"amenity": "Baseball Stadium",
		"popupContent": "This is where the Rockies play!"
	},
	"geometry": {
		"type": "Point",
		"coordinates": [-104.99404, 39.75621]
	}
};

L.geoJSON(geojsonFeature, {
	onEachFeature: onEachFeature
}).addTo(map);</code></pre>

<h4>filter</h4>

<p><code>filter</code> 选项可用于控制 GeoJSON feature 的可见性。为了达到这个目的，我们传递一个函数作为 <code>filter</code> 选项。这个函数为您的 GeoJSON 图层中的每个 feature 被调用，并被传递给 <code>feature</code> 和 code>layer</code>。然后你可以利用特征的属性值，通过返回 <code>true</code> 或 <code>false</code> 来控制可见性。</p>

<p>在下面的例子中，"Busch Field "将不会显示在地图上。</p>

<pre><code>var someFeatures = [{
	"type": "Feature",
	"properties": {
		"name": "Coors Field",
		"show_on_map": true
	},
	"geometry": {
		"type": "Point",
		"coordinates": [-104.99404, 39.75621]
	}
}, {
	"type": "Feature",
	"properties": {
		"name": "Busch Field",
		"show_on_map": false
	},
	"geometry": {
		"type": "Point",
		"coordinates": [-104.98404, 39.74621]
	}
}];

L.geoJSON(someFeatures, {
	filter: function(feature, layer) {
		return feature.properties.show_on_map;
	}
}).addTo(map);</code></pre>

<p>查看<a href="example.html">示例页面</a>，详细了解 GeoJSON 图层的功能。</p>
