---
layout: v2
title: Download
bodyclass: download-page
---

## 下载 Leaflet

<table>
	<tr>
		<th>版本</th>
		<th>说明</th>
	</tr>
	<tr>
		<td><a href="http://cdn.leafletjs.com/leaflet/v1.6.0/leaflet.zip">Leaflet 1.6.0</a></td>
		<td>稳定版，于2019年11月17日发布。</td>
	</tr>
	<tr>
		<td><a href="https://leafletjs-cdn.s3.amazonaws.com/content/leaflet/master/leaflet.zip">Leaflet 1.7-dev</a></td>
		<td>开发版，在master分支上开发。</td>
	</tr>
	<tr>
		<td class="width100"><a href="http://cdn.leafletjs.com/leaflet/v0.7.7/leaflet.zip">Leaflet 0.7.7</a></td>
		<td>旧版，于2013年11月18日发布，最新更新于2015年10月26日。</td>
	</tr>
</table>

[查看更新日志](https://github.com/Leaflet/Leaflet/blob/master/CHANGELOG.md)

请注意，主版本可能包含不兼容的更改，因此在升级到主版本时，请仔细阅读更改日志。

[获取有关新版Leaflet的通知](https://github.com/Leaflet/Leaflet/issues/6295)

### 使用Leaflet的托管版本

最新的Leaflet稳定版已在多个CDN上提供。使用时，直接将其放在HTML代码的开头即可：

    <link rel="stylesheet" href="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.css" />
    <script src="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.js"></script>

为避免潜在的安全问题，我们建议并鼓励在使用CDN中的Leaflet时启用[subresource integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity):

    <link rel="stylesheet" href="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.css"
      integrity="{{site.integrity_hash_css}}"
      crossorigin=""/>
    <script src="https://unpkg.com/leaflet@{{ site.latest_leaflet_version}}/dist/leaflet.js"
      integrity="{{site.integrity_hash_uglified}}"
      crossorigin=""></script>

Leaflet 当前可以使用的免费CDN:  [unpkg](https://unpkg.com/leaflet/dist/), [cdnjs](https://cdnjs.com/libraries/leaflet), [jsDelivr](https://www.jsdelivr.com/package/npm/leaflet?path=dist)

免责声明：这些服务是Leaflet的外部服务； 如有疑问或需要支持，请直接与他们联系。

### 使用下载版的 Leaflet

在从上述链接下载到本地的文件中，您将看到以下文件：

- `leaflet.js` - 这是压缩后的Leaflet JavaScript代码。
- `leaflet-src.js` - 这是可读的，最小的Leaflet JavaScript，有时对调试很有帮助。<small>(该文件完整的哈希值为 <nobr><tt>{{site.integrity_hash_source}}</tt></nobr>)</small>
- `leaflet.css` - 这是 Leaflet 的样式文件。
- `images` - 这是一个文件夹，其中包含leaflet.css引用的图像。 它必须与leaflet.css位于同一目录中。

将下载的文件解压到您网站的目录中，并将其添加到HTML代码的开头:

    <link rel="stylesheet" href="/path/to/leaflet.css" />
    <script src="/path/to/leaflet.js"></script>

### 使用JavaScript包管理器

如果使用[`npm`软件包管理器](https://www.npmjs.com/)，则可以通过运行以下命令安装Leaflet：

    npm install leaflet

您可以在`node_modules/leaflet/dist`中找到Leaflet发行文件。

### Leaflet 源码

上面的这些下载软件包仅包含库本身。 如果要下载完整的源代码，包括单元测试，调试文件，构建脚本等，则可以从<a href="https://github.com/Leaflet/Leaflet">GitHub repository</a><a href="https://github.com/Leaflet/Leaflet/releases">下载</a>。

### 从源代码中构建 Leaflet

Leaflet构建系统由[Node.js](http://nodejs.org)平台提供支持，该平台易于安装并且在所有主要平台上均能正常运行。 设置步骤如下：

 1. [下载并安装 Node](http://nodejs.org)
 2. 在命令行中运行以下命令:

 <pre><code>npm install</code></pre>

现在已经安装了所有内容，然后在Leaflet目录中运行`npm run build`。 这将合并并压缩Leaflet源文件，将构建保存到dist文件夹。

