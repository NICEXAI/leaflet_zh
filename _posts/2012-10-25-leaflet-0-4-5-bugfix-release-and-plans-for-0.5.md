---
layout: post
title: Leaflet 0.4.5 Bugfix 版发布 以及 0.5 的计划
description: Leaflet 0.4.5 正式发布, 包含针对即将推出的 Chrome 23+（目前为测试版）和 IE10 的小而重要的缩放动画错误修复。未来 0.5 版本的开发工作仍在继续
author: Vladimir Agafonkin
authorsite: http://agafonkin.com/en
---

### 0.4.5 发布

当我们继续为下一个主要版本（ 0.5 ）工作时，今天我们决定发布 Leaflet 0.4.5 。它只包含一个小但重要的 bug 修复，即在即将到来的 Chrome 23 （目前处于测试阶段，将在几周内发布）和 Internet Explorer 10 （除了 Windows 8 之外，最终将进入 Windows 7 ）上的 wonky 缩放动画。

我们鼓励每个人都进行升级（在 Chrome 23 变成稳定版之前）。一如既往，你可以在 [下载页面](.../.../.../download.html) 找到新版本的 CDN 链接和下载。

### 0.5 的计划

随着 Leaflet 接近功能完整的状态和 API 的稳定，我们自然而然地将重点从新功能转向性能和可用性的改进，更好的浏览器和设备支持，错误修复和内部重构，使 Leaflet 的某些部分（如投影和矢量渲染）更容易为插件开发者和高级用户扩展和定制。

在 `master` 分支中已经实现的亮点包括对 **IE10 触摸设备和 Metro 应用程序的触摸交互支持**，以及更流畅、更灵敏的平移惯性。更多细节请关注 [完整更新日志](https://github.com/Leaflet/Leaflet/blob/master/CHANGELOG.md) 。

我们也正在对矢量渲染代码进行重大的重构，以允许用自定义形状、额外的渲染系统（如现有的 SVG、VML 和 Canvas 渲染器之外的 WebGL ）对基本功能进行更简单的扩展，在渲染器之间轻松切换，也使代码更简单、更容易理解。

投影相关的代码也是如此，使使用 Leaflet 的非标准投影更容易，包括游戏和室内地图的普通投影。由于这些变化，除了让先进的 GIS 人士更高兴之外，我们还将看到更多令人敬畏的 Leaflet 项目，如 [ IGN 上的交互式 Skyrim 地图](http://www.ign.com/wikis/the-elder-scrolls-5-skyrim/interactive-maps/Skyrim) 或 [ Wowhead 上的魔兽世界地图](http://www.wowhead.com/map) 。

即将到来的几周的另一个重要任务是与插件开发者更紧密地合作。特别是，重点领域之一将是 [Leaflet.draw](https://github.com/jacobtoye/Leaflet.draw) 插件，它将很快成为最先进的地图矢量绘制/编辑解决方案，就像 Dave 的 [Leaflet.markercluster](https://github.com/danzel/Leaflet.markercluster) 成为所有地图平台中最好的标记聚类解决方案。

目前的计划是在 11 月中旬的某个时候发布 0.5 稳定版。请继续关注!

### 为 Leaflet 投稿

Leaflet 是一个真正的开源项目，所以我们总是很高兴认识新的贡献者，接受补丁和错误报告。为了帮助其他人参与 Leaflet 的开发，并使管理贡献更容易，我放了一个 [贡献于 Leaflet ](https://github.com/Leaflet/Leaflet/blob/master/CONTRIBUTING.md) 指南，其中有最佳实践和建议 &mdash; 请看!

感谢大家! Leaflet 有一个相当惊人的社区，这让我非常自豪。继续努力吧!

Cheers,<br />
Vladimir, Leaflet author and maintainer.
