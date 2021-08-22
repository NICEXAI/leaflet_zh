---
layout: post
title: Leaflet 插件开发指南
description: 一些可以帮助您发布一款优秀的 Leaflet 插件的最佳实践和技巧
author: Vladimir Agafonkin
authorsite: http://agafonkin.com/en
---

Leaflet 最伟大的地方之一是它强大的插件生态系统。
[Leaflet 插件页面](https://leafletjs.com/plugins.html) 列出了几十个很棒的插件，而且每周都会有更多的插件加入。

本指南列出了一些发布符合 Leaflet 本身质量标准的 Leaflet 插件的最佳实践。也可[在 repo](https://github.com/Leaflet/Leaflet/blob/master/PLUGIN-GUIDE.md) 。

### 演示文稿

#### 存储库

把你的 Leaflet 插件放在一个单独的 [GitHub](http://github.com) 仓库里是最好的。
如果你创建了一个用于不同用途的插件集合，
不要把它们放在一个版本库里 &mdash;
通常情况下，在单个仓库中使用小型、独立的插件会更容易。

#### 演示

在发布一个插件时，最重要的事情是包括一个演示，展示该插件的功能 &mdash;
这通常是人们要找的第一件事。

放置演示的最简单方法是使用 [GitHub Pages](http://pages.github.com/) 。
一个好的 [起点](https://help.github.com/articles/creating-project-pages-manually) 是在你的 repo 中创建一个 `gh-pages` 分支并在其中添加一个 `index.html` 页面 &mdash;
推送后，它将被发布为 `http://<user>.github.io/<repo>` 。

#### 阅读手册

接下来你需要有一个描述性的 `README.md` 在 repo 的根部(或一个有类似内容的网站的链接)。
它至少应包含以下项目：

- 插件的名称
- 简单扼要地描述它的作用
- 要求
	- Leaflet 版本
	- 其他外部依赖(如果有的话)
	- 浏览器、设备兼容性
- 演示链接
- 包括该插件的说明
- 简单的使用代码示例
- API 参考(方法、选项、事件)。

#### 许可证

每个开放源码库都应该包括一个许可证。
如果你不知道该为你的代码选择什么样的开源许可证。
[MIT License](http://opensource.org/licenses/MIT) 和 [BSD 2-Clause License](http://opensource.org/licenses/BSD-2-Clause) 都是不错的选择。
你可以把它作为 `LICENSE` 文件放在 repo 中，或者直接从 Readme 链接到许可证。

### 编码

#### 文件结构

保持文件结构的干净和简单，
不要在一个地方堆积大量的文件 &mdash;
让新人在你的 repo 中容易找到自己的方向。

一个简单的插件的原始版本应该是这样的：

	my-plugin.js
	README.md

一个更复杂的插件的文件结构的例子：

	/src        JS source files
	/dist       minified plugin JS, CSS, images
	/spec       test files
	/examples   HTML examples of plugin usage
	README.md
	LICENSE
	package.json

#### 代码公约

每个人的口味都不同，但重要的是，无论你为你的插件选择什么惯例，都要保持一致。

要想有一个好的起点，请查看 [Airbnb JavaScript 指南](https://github.com/airbnb/javascript) 。
Leaflet 几乎遵循同样的惯例
除了使用智能制表符(硬制表符用于缩进，空格用于对齐)之外
和在 `function` 关键词后面加一个空格。

#### 插件 API

不要在你的插件中暴露全局变量。<br>
如果你有一个新的类，直接把它放在 `L` 命名空间( `L.MyPlugin` )。<br>
如果你继承了一个现有的类，让它成为一个子属性( `L.TileLayer.Banana` )。<br>
如果你想给现有的 Leaflet 类添加新方法，你可以这样做。`L.Marker.include({myPlugin: ...})` 。

函数、方法和属性名称应使用 `camelCase` 。<br>
类名应使用 `大写的 CamelCase` 。

如果你的函数中有很多参数，可以考虑接受一个选项对象来代替(尽可能放上默认值，这样用户就不需要指定所有的参数)：

	// bad
	marker.myPlugin('bla', 'foo', null, {}, 5, 0);

	// good
	marker.myPlugin('bla', {
		optionOne: 'foo',
		optionThree: 5
	});

而最重要的是，保持简单。Leaflet 是关于*简单的*。

Cheers,<br>
Vladimir.
