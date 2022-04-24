---
layout: tutorial_v2
title: A guide to basic Leaflet accessibility
---

## 无障碍地图

[Web accessibility](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
是一种包容性的做法，确保不存在任何妨碍互动或信息获取的障碍。

这个 Leaflet 无障碍指南可以帮助你创建一个让残障人士也能够使用的地图。

### 保留有用的默认值

Leaflet 预设了一套有用的默认值。

默认情况下，地图 container 和 markers 可以使用键盘进行操作。
这使得那些无法使用指向性设备的用户能够正常使用。
在更改诸如此类的默认值之前，请考虑对用户的影响。

### Markers 必须被标记

在使用 markers 时,
必须确保每个 marker 都有一个独特的、描述性的
[`alt`](/reference.html#marker-alt)
或
[`title`](/reference.html#marker-alt)。

<pre><code class="javascript">var marker = L.marker([50.4501, 30.5234],
  {alt: 'Kyiv'}).addTo(map) // "Kyiv" is the <a href="https://www.w3.org/TR/accname-1.1/#dfn-accessible-name"><em>accessible name</em></a> of this marker
  .bindPopup('Kyiv, Ukraine is the birthplace of Leaflet!');</code></pre>

生成可被[屏幕阅读器](https://en.wikipedia.org/wiki/Screen_reader)识别的标记：

{% include frame.html url="example.html" width=600 height=400 %}

在 `divIcon` 的情况下。
[自定义 HTML](reference.html#divicon-html)
可以以其他方式提供一个视觉或非视觉的标签。

### 测试你的地图

发现可访问性问题的最好方法就是只用键盘或屏幕阅读器来测试你的地图。
你可能已经有一个预装的屏幕阅读器，比如说：

- Windows 上的 [Narrator](https://support.microsoft.com/en-us/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)
- Linux 上的 [Orca](https://help.gnome.org/users/orca/stable/index.html.en)
- Android 上的 [TalkBack](https://support.google.com/accessibility/android/answer/6283677?hl=en)
- [macOS](https://support.apple.com/guide/voiceover/welcome/mac) 和 [iOS](https://support.apple.com/guide/iphone/turn-on-and-practice-voiceover-iph3e2e415f/ios) 上的 VoiceOver

### 纯粹的装饰性地图

有些地图[纯粹是装饰性的](https://www.w3.org/TR/WCAG21/#dfn-pure-decoration)，并不打算让用户与之互动（类似于背景图片和视频的方式）。

此类地图并没有可聚焦的后代，应该对辅助技术 (AT) 隐藏。这是为了避免混淆屏幕阅读器用户的可能性，并为键盘用户删除任何不必要的制表位。
实现此目的的一种简单方法是使用 HTML
[`inert` 属性](https://github.com/WICG/inert)，
比如：

```html
<!-- This map is for aesthetic purposes only, and can not be interacted with! -->
<div id='decorative-map' inert></div>
<script src='https://unpkg.com/wicg-inert@latest/dist/inert.min.js'></script>
```

### 使用插件

[插件](plugins.html)可以增强用户的体验，但在某些情况下也会降低体验。因此， 每当添加新插件时，[测试你的地图](#test-your-maps)则显示非常重要。

如果你在插件中发现可访问性问题，请向插件作者报告。

[Leaflet.fullscreen](https://github.com/Leaflet/Leaflet.fullscreen) 插件就是一个可以增强用户体验的插件示例 。通过允许用户进入全屏模式，他们可以孤立地探索地图，集中注意力，这对键盘和屏幕阅读器用户特别有帮助（因为他们不太可能无意中在地图外导航），而且也包括一般的移动用户。

### 使用最新版本的 Leaflet

Leaflet 正在不断提高可访问性，
使用最新的稳定
[版本](/download.html)
以获得最大的功能体验！
