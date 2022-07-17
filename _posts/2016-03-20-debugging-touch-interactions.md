---
layout: post
title: 调试触控的交互
description: 有时候你需要创建一个新的工具来调试 Leaflet
author: Iván Sánchez
authorsite: http://ivan.sanchezortega.es
---


大多数时候，修复 Leaflet 代码中的错误是很容易的。代码很简单，容易阅读(大部分情况下)，结构良好。代码惯例和单元测试使新人很容易尝试对核心代码进行一些修改。在过去的几个月里，我们向 [Your First PR](https://yourfirstpr.github.io/) 的朋友们发送了一些简单的错误报告——我们喜欢看到第一次来的人对 Leaflet 的修复做出贡献!


维护、开发像 Leaflet 这样的 javascript 库的一些困难是要确保所有东西都能在每一个主要的浏览器上运行。一个在 Ubuntu 桌面上的 Firefox 上运行的技术，在 Macbook 上的 Safari 上可能会出现故障；一个在 Windows 10 上的 Edge 上运行的技术，在 Android 上的 Chrome 上可能会完全失效。

幸运的是，通过查看代码中的 [对 `L.Browser` 的引用](https://github.com/search?q=Browser+repo%3ALeaflet%2FLeaflet+language%3AJavaScript+extension%3Ajs+path%3A%2Fsrc&ref=searchresults&type=Code&utf8=%E2%9C%93) ，可以轻易看到 Leaflet 中所有的浏览器专用黑客。

这有时会导致一些 [不理想的代码](https://github.com/Leaflet/Leaflet/blob/master/src/dom/DomEvent.DoubleTap.js#L65)：

<pre><code class="javascript">    // 在一些平台上（特别是 win10 上的 chrome + 触摸屏 + 鼠标）,
    // 浏览器不会触发 touchend / pointerup 事件，但会触发
    // 原生的双击。见 #4127 。
    if (!L.Browser.edge) {
    	obj.addEventListener('dblclick', handler, false);
    }
</code></pre>

浏览器开发者不止一次告诉我，浏览器嗅探是错误的，而特征检测是正确的。我的意思是，检测 3D CSS 变换和 HTML5 `<video>` 支持很容易，但没有(理智的)方法来检测浏览器在双击触摸屏时是否自己发射了 `dblclick` 事件。

调试触摸交互特别棘手。有时重现一个触摸交互错误的条件很简单(在同一位置双击触摸屏)，但有时却更具体。在 [#3798](https://github.com/Leaflet/Leaflet/issues/3798) 和 [#3814](https://github.com/Leaflet/Leaflet/issues/3814) 中，条件是"用一个手指拖动，然后放下另一个手指并捏住"，而在 [#3530](https://github.com/Leaflet/Leaflet/issues/3530) 中是 "捏住直到达到 `maxZoom`，然后做双指拖动"。

这种 bug 的问题在于，它们在受控条件下的重现是**令人沮丧的**，而且是**耗时的**。想象一下，当你有一个代码编辑器和一个浏览器调试器的时候，同时用两只手在看调试器的时候做一个非常特殊的触摸手势。然后你想在调试器中检查一个变量，但你不能移动你的手指，哪怕是一个像素，因为那会运行更多的代码并改变状态。

然后，在过去的一个小时里，第五次，摇晃的手机充电器连接器再次摇晃，调试器断开连接，你不得不重新开始。

<table class="image">
<!-- <caption align="bottom"><small></small></caption> -->
<tr><td style='text-align:center'><img src="https://i.chzbgr.com/full/4896152320/h3FAAE99E/" alt="rage quit"/></td></tr>
</table>

如果我有一两只多余的手，调试触摸互动就会简单得多，但生物技术离让我多长出一只手还很遥远。

幸运的是，我们可以利用 [向浏览器调度自定义事件](https://developer.mozilla.org/docs/Web/API/EventTarget/dispatchEvent) 。通常，当我们使用鼠标(或触摸板，或触摸屏，或数字板)时，网络浏览器会产生一个 [`MouseEvent`](https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent) (或 [`TouchEvent`](https://developer.mozilla.org/docs/Web/API/TouchEvent) 或 [`PointerEvent`](https://developer.mozilla.org/docs/Web/API/PointerEvent) 。但是，我们的 javascript 程序员可以创建一个合成的(即假的)事件，然后把它扔给浏览器，这样它就可以把它派发给任何正在监听事件的代码。

不幸的是，创建和分配这些事件是很麻烦的。一个触摸手势至少需要 4 到 8 个事件，以特定的顺序、特定的数据和特定的时间进行。已经有一些人尝试将其自动化(我能找到的最好的是 [hammer.js simulator](https://github.com/hammerjs/simulator) ，但没有好的方法来模拟复杂的自定义触摸手势。

直到现在。

我很自豪地介绍 [**假手**](https://github.com/Leaflet/prosthetic-hand) ，以满足你所有需要多出一只手的 javascript 调试需要。

用假手，我现在可以在 Leaflet 网页上自动进行捏合缩放的手势了：


<table class="image">
<caption align="bottom"><small>You get to see my disembodied fingers as a bonus</small></caption>
<tr><td style='text-align:center'><img src="/docs/images/2016-03-20-prosthetic-hand-zooming.gif" alt="Animated screenshot of prosthetic-hand zooming in and out"/></td></tr>
</table>


装上这个库后，只需要求一个额外的手(有特定的计时模式)即可：
<pre><code class="javascript">var h = new Hand({ timing: 'frame' });
</code></pre>

然后长出一些手指:
<pre><code class="javascript">var f1 = h.growFinger('touch');
var f2 = h.growFinger('touch');
</code></pre>

然后移动手指(使用像素坐标和毫秒)：
<pre><code class="javascript">f1.wait(100).moveTo(250, 200, 0)
	.down().wait(500).moveBy(-200, 0, 1000).wait(500).up().wait(500)
	.down().wait(500).moveBy( 200, 0, 1000).wait(500).up().wait(500);

f2.wait(100).moveTo(350, 200, 0)
	.down().wait(500).moveBy( 200, 0, 1000).wait(500).up().wait(500)
	.down().wait(500).moveBy(-200, 0, 1000).wait(500).up().wait(500);
</code></pre>

你可以在 [现场假手演示](https://leaflet.github.io/prosthetic-hand/demos/) 中查看这一点。

义肢库并不完美，有些类型的事件只在某些浏览器中起作用，但它可以帮助以可重复的方式触发鼠标、触摸、指针事件，并可调整时间，使开发人员能够在调试器中保持双手。计时模式允许对触发的事件进行细化控制，允许为同样的手势运行更少的代码迭代，这反过来意味着更简单、更好地理解正在发生的事情。

---

有一句名言(经常 [误认为是亚伯拉罕-林肯](http://quoteinvestigator.com/2014/03/29/sharp-axe/) 说：

<blockquote>A woodsman was once asked, "What would you do if you had just five minutes to chop down a tree?" He answered, "I would spend the first two and a half minutes sharpening my axe."</blockquote>

网络开发也不例外——拥有正确的工具将使你的任务变得更加容易。

这不仅仅是一个时间问题。也许从头开始写一个工具是很耗时的，但最好的收获是，调试**不再令人沮丧**。以前，它是 "在触摸屏上用一只手，仔细看调试器，不要使用断点，因为你的手不够用"。现在是 "改变假手事件的时间，设置断点，**轰**"。

而更棒的是，拥有一个自动化工具意味着 Leaflet 现在有了 [**触摸交互的单元测试**](https://github.com/Leaflet/Leaflet/blob/master/spec/suites/map/handler/Map.TouchZoomSpec.js) 。PhantomJS 无头网页浏览器可以理解义肢产生的  `TouchEvent`s，并可以检查地图在执行该手势时是否有预期的行为。

通过自动化的触摸测试，我们在 Leaflet 中节省的时间和麻烦将是巨大的。我们只能希望更多的项目能从类似的自动化测试中受益。

---

不要只写开源代码。为每个人制作更好的工具。

Yours,
Iván