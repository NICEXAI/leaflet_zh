---
layout: tutorial_v2
title: Interactive Choropleth Map
---

## 交互式 Choropleth 地图

这是一个使用 [GeoJSON](.../geojson/) 和一些[自定义控件](/reference.html#control)创建美国各州人口密度的彩色交互式 [choropleth map](http://en.wikipedia.org/wiki/Choropleth_map) 的研究案例（希望能说服所有尚未使用 Leaflet 的主要新闻和政府网站开始这样做）。

该教程的灵感来自于 [Ryan Murphy](http://www.texastribune.org/about/staff/ryan-murphy/) 制作的[《德克萨斯论坛报》美国参议院决选结果地图](http://www.texastribune.org/library/data/us-senate-runoff-results-map/)（同样由 Leaflet 提供）。

{% include frame.html url="example.html" width=816 height=516 %}

### Data Source

我们将创建一个美国各州人口密度的可视化图。由于数据量（各州的形状和各州的密度值）不是很大，最方便和简单的方法是使用 [GeoJSON](../geojson/) 来存储，然后显示。

我们的 GeoJSON 数据（[us-states.js](us-states.js)）的每个 feature 将看起来像这样：

	{
		"type": "Feature",
		"properties": {
			"name": "Alabama",
			"density": 94.65
		},
		"geometry": ...
		...
	}

该州的 GeoJSON 数据是由 [D3](http://d3js.org/) 的 [Mike Bostock](http://bost.ocks.org/mike) 根据[美国人口普查局](http://www.census.gov/)2011年7月1日的数据制作然后友情分享的，用[本维基百科文章](http://en.wikipedia.org/wiki/List_of_U.S._states_by_population_density)的密度值进行了扩展，并赋值给 `statesData` JS 变量。

### 基本州地图

让我们在地图上显示我们的州的数据:

	var map = L.map('map').setView([37.8, -96], 4);

	var tiles = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
		maxZoom: 19,
		attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
	}).addTo(map);

	L.geoJson(statesData).addTo(map);

{% include frame.html url="example-basic.html" %}


### 添加一些颜色

现在我们需要根据各州的人口密度为其着色。为地图选择漂亮的颜色可能很麻烦，但有一个很好的工具可以帮助我们------[ColorBrewer]（http://colorbrewer2.org/）。使用我们从它那里得到的值，我们创建一个函数，根据人口密度返回一个颜色：

	function getColor(d) {
		return d > 1000 ? '#800026' :
		       d > 500  ? '#BD0026' :
		       d > 200  ? '#E31A1C' :
		       d > 100  ? '#FC4E2A' :
		       d > 50   ? '#FD8D3C' :
		       d > 20   ? '#FEB24C' :
		       d > 10   ? '#FED976' :
		                  '#FFEDA0';
	}

接下来，我们为 GeoJSON 层定义一个样式函数，使其 `fillColor` 依赖于 `feature.properties.density` 属性，同时也对外观进行一些调整，用虚线添加一个漂亮的点缀。

	function style(feature) {
		return {
			fillColor: getColor(feature.properties.density),
			weight: 2,
			opacity: 1,
			color: 'white',
			dashArray: '3',
			fillOpacity: 0.7
		};
	}

	L.geoJson(statesData, {style: style}).addTo(map);

现在看起来好多了！

{% include frame.html url="example-color.html" %}


### 添加交互

现在，让我们在鼠标悬停时以某种方式在视觉上突出显示状态。首先，我们要为 "mouseover" 事件定义一个事件监听器：

	function highlightFeature(e) {
		var layer = e.target;

		layer.setStyle({
			weight: 5,
			color: '#666',
			dashArray: '',
			fillOpacity: 0.7
		});

		if (!L.Browser.ie && !L.Browser.opera && !L.Browser.edge) {
			layer.bringToFront();
		}
	}

在这里，我们通过 `e.target` 访问被悬停的图层，在图层上设置一个厚厚的灰色边框作为我们的高亮效果，同时把它放到图层最前面，这样边框就不会与附近的状态发生冲突（但对 IE、Opera 或 Edge 来说不是这样，因为它们在 `mouseover ` 时使用 ` bringToFront` 有问题）。

接下来我们将定义鼠标 `mouseout` 时发生的事情:

	function resetHighlight(e) {
		geojson.resetStyle(e.target);
	}

`geojson.resetStyle` 方法可以很方便的将图层样式重置为默认状态（由我们的 `style` 函数定义）。为了让这个方法起作用，请确保我们的 GeoJSON 图层可通过 `geojson` 变量访问，方法是在我们的监听器之前定义它，然后再将图层分配给它：

	var geojson;
	// ... our listeners
	geojson = L.geoJson(...);

添加一个额外的操作， 让我们定义一个 `click` 来监听缩放状态的变更:

	function zoomToFeature(e) {
		map.fitBounds(e.target.getBounds());
	}

现在我们将使用 `onEachFeature` 选项在我们的状态层上添加监听器（listeners）：

	function onEachFeature(feature, layer) {
		layer.on({
			mouseover: highlightFeature,
			mouseout: resetHighlight,
			click: zoomToFeature
		});
	}

	geojson = L.geoJson(statesData, {
		style: style,
		onEachFeature: onEachFeature
	}).addTo(map);

这使得状态在悬停时被很好地突出，并使我们有能力在监听器中添加其他的交互。

### Custom Info Control

我们可以使用通用的点击弹出窗口来显示不同状态的信息，但我们将选择一条不同的途径---在一个[自定义控件](/reference.html#control)内的状态悬停时显示。

这是我们控件的代码:

Here's the code for our control:

	var info = L.control();

	info.onAdd = function (map) {
		this._div = L.DomUtil.create('div', 'info'); // create a div with a class "info"
		this.update();
		return this._div;
	};

	// method that we will use to update the control based on feature properties passed
	info.update = function (props) {
		this._div.innerHTML = '<h4>US Population Density</h4>' +  (props ?
			'<b>' + props.name + '</b><br />' + props.density + ' people / mi<sup>2</sup>'
			: 'Hover over a state');
	};

	info.addTo(map);

我们需要在用户将鼠标悬停在某个状态上时更新控件，因此我们还将修改我们的侦听器（listeners），如下所示：

	function highlightFeature(e) {
		...
		info.update(layer.feature.properties);
	}

	function resetHighlight(e) {
		...
		info.update();
	}

该控件还需要一些 CSS 样式才能看起来不错：

{: .css}
	.info {
		padding: 6px 8px;
		font: 14px/16px Arial, Helvetica, sans-serif;
		background: white;
		background: rgba(255,255,255,0.8);
		box-shadow: 0 0 15px rgba(0,0,0,0.2);
		border-radius: 5px;
	}
	.info h4 {
		margin: 0 0 5px;
		color: #777;
	}

### 自定义图例控件

创建带有图例的控件更容易，因为它是静态的并且不会在状态悬停时改变。JavaScript 代码：

	var legend = L.control({position: 'bottomright'});

	legend.onAdd = function (map) {

		var div = L.DomUtil.create('div', 'info legend'),
			grades = [0, 10, 20, 50, 100, 200, 500, 1000],
			labels = [];

		// loop through our density intervals and generate a label with a colored square for each interval
		for (var i = 0; i < grades.length; i++) {
			div.innerHTML +=
				'<i style="background:' + getColor(grades[i] + 1) + '"></i> ' +
				grades[i] + (grades[i + 1] ? '&ndash;' + grades[i + 1] + '<br>' : '+');
		}

		return div;
	};

	legend.addTo(map);

控件的 CSS 样式（我们也重复使用前面定义的 `info` 类）:

{: .css}
	.legend {
		line-height: 18px;
		color: #555;
	}
	.legend i {
		width: 18px;
		height: 18px;
		float: left;
		margin-right: 8px;
		opacity: 0.7;
	}

请在页面顶部或者[单独的页面](example.html)上的查看具体效果。
