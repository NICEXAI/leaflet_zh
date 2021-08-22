---
layout: tutorial_v2
title: Markers With Custom Icons
---

## 带有自定义图标的标记

在本教程中，你将学习如何轻松定义你自己的图标并放在地图上作为标记使用。

{% include frame.html url="example.html" %}

### Preparing the images

要制作一个自定义的图标，我们通常需要两张图片---实际的图标图片和它的阴影图片。在本教程中，我们采用了Leaflet的标志，并从中创建了四张图片---3张不同颜色的叶子图片和一张阴影图片。

<p>
	<img style="border: 1px solid #ccc" src="leaf-green.png" />
	<img style="border: 1px solid #ccc" src="leaf-red.png" />
	<img style="border: 1px solid #ccc" src="leaf-orange.png" />
	<img style="border: 1px solid #ccc" src="leaf-shadow.png" />
</p>

请注意，图像中的白色区域实际上是透明的。

### Creating an icon

Leaflet中的标记图标是由[L.Icon](/reference.html#icon)对象定义的，在创建标记时，它被作为一个选项传递。让我们来创建一个绿叶图标。

	var greenIcon = L.icon({
		iconUrl: 'leaf-green.png',
		shadowUrl: 'leaf-shadow.png',

		iconSize:     [38, 95], // size of the icon
		shadowSize:   [50, 64], // size of the shadow
		iconAnchor:   [22, 94], // point of the icon which will correspond to marker's location
		shadowAnchor: [4, 62],  // the same for the shadow
		popupAnchor:  [-3, -76] // point from which the popup should open relative to the iconAnchor
	});

现在，在地图上放一个带有这个图标的标记是很容易的。

	L.marker([51.5, -0.09], {icon: greenIcon}).addTo(map);

{% include frame.html url="example-one-icon.html" %}

### 定义一个图标类（Class）

如果我们需要创建几个有很多共同点的图标，怎么办？让我们定义我们自己的图标类，包含共享选项，继承于`L.Icon`! 在Leaflet中，这真的很简单。

	var LeafIcon = L.Icon.extend({
		options: {
			shadowUrl: 'leaf-shadow.png',
			iconSize:     [38, 95],
			shadowSize:   [50, 64],
			iconAnchor:   [22, 94],
			shadowAnchor: [4, 62],
			popupAnchor:  [-3, -76]
		}
	});

现在我们可以从这个类中创建所有的带有三个叶子的图标并使用它们。

	var greenIcon = new LeafIcon({iconUrl: 'leaf-green.png'}),
		redIcon = new LeafIcon({iconUrl: 'leaf-red.png'}),
		orangeIcon = new LeafIcon({iconUrl: 'leaf-orange.png'});

你可能已经注意到，我们使用`new`关键字来创建LeafIcon实例。那么为什么所有的Leaflet类在创建时都没有使用它呢？答案很简单：真正的Leaflet类是用大写字母命名的(例如`L.Icon`)，它们也需要用`new`来创建，但也有一些小写名字的快捷方式(`L.icon`)，是为了方便而创建的，比如这样。

	L.icon = function (options) {
		return new L.Icon(options);
	};

你也可以对你的 classes 做同样的事情。好了，让我们最后在地图上放一些带有这些图标的标记。

	L.marker([51.5, -0.09], {icon: greenIcon}).addTo(map).bindPopup("I am a green leaf.");
	L.marker([51.495, -0.083], {icon: redIcon}).addTo(map).bindPopup("I am a red leaf.");
	L.marker([51.49, -0.1], {icon: orangeIcon}).addTo(map).bindPopup("I am an orange leaf.");

就这样了。现在看看[完整的例子](example.html)，[`L.Icon` docs](/reference.html#icon)，或者浏览一下[其他例子](.../.../examples.html)。
