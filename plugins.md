---
layout: v2
title: Plugins
bodyclass: plugins-page
---

## Leaflet 插件

Leaflet的目的是尽可能轻巧，并着重于一组核心功能，而扩展其功能的一种简单方法是使用第三方插件。 感谢Leaflet背后的强大社区，提供了数百个不错的插件供大家选择。

---

<div id="toc" class="clearfix">
	<div class="toc-col">
		<h4>Tile &amp; Image 图层</h4>
		<ul>
			<li> <a href='#basemap-providers'>底图提供程序</a></li>
			<li> <a href='#basemap-formats'>底图格式</a></li>
			<li> <a href='#non-map-base-layers'>Non-map 基础图层</a></li>
			<li> <a href='#tileimage-display'>Tile/Image 显示</a></li>
			<li> <a href='#tile-load'>Tile 加载</a></li>
			<li> <a href='#vector-tiles'>矢量 Tile</a></li>
		</ul>
		<h4>叠加数据</h4>
		<ul>
			<li> <a href='#overlay-data-formats'>叠加数据格式</a></li>
			<li> <a href='#dynamiccustom-data-loading'>动态加载数据</a></li>
			<li> <a href='#synthetic-overlays'>合成叠加的数据</a></li>
			<li> <a href='#data-providers'>数据提供程序</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>叠加显示</h4>
		<ul>
			<li><a href="#markers--renderers">标记 &amp; 渲染</a></li>
			<li><a href="#overlay-animations">叠加动画</a></li>
			<li><a href="#clusteringdecluttering">Clustering/decluttering</a></li>
			<li><a href="#heatmaps">热力图</a></li>
			<li><a href="#dataviz">数据可视化</a></li>
		</ul>
		<h4>叠加交互</h4>
		<ul>
			<li><a href="#edit-geometries">编辑几何图形</a></li>
			<li><a href="#time--elevation">时间 &amp; 海拔</a></li>
			<li><a href="#search--popups">搜索 &amp; 弹出框</a></li>
			<li><a href="#areaoverlay-selection">区域/覆盖选择</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>地图交互</h4>
		<ul>
			<li><a href="#layer-switching-controls">控制图层切换</a></li>
			<li><a href="#interactive-panzoom">交互式平移/缩放</a></li>
			<li><a href="#bookmarked-panzoom">带书签的平移/缩放</a></li>
			<li><a href="#fullscreen-controls">全屏</a></li>
			<li><a href="#minimaps--synced-maps">小地图 &amp; 同步地图</a></li>
			<li><a href="#measurement">测量</a></li>
			<li><a href="#mouse-coordinates">鼠标坐标</a></li>
			<li><a href="#events">事件</a></li>
			<li><a href="#user-interface">用户界面</a></li>
			<li><a href="#printexport">打印/导出</a></li>
			<li><a href="#geolocation">地理位置</a></li>
		</ul>
	</div>
	<div class="toc-col">
		<h4>各种各样的</h4>
		<ul>
			<li><a href="#geoprocessing">地理处理</a></li>
			<li><a href="#routing">路由</a></li>
			<li><a href="#geocoding">地理编码</a></li>
			<li><a href="#plugin-collections">插件集合</a></li>
		</ul>
		<h4>综合的</h4>
		<ul>
			<li><a href="#frameworks--build-systems">框架 &amp; 构建系统</a></li>
			<li><a href="#3rd-party-integration">3<sup>rd</sup> party</a></li>
		</ul>
		<hr>
		<a href="#develop-your-own">开发属于自己的插件</a>
	</div>
</div>


## Tile &amp; Image 图层

下面的插件支持加载不同的地图并提供 Tile 和 Image 图层的功能。

* [Basemap providers](#basemap-providers)
* [Basemap formats](#basemap-formats)
* [Non-map base layers](#non-map-base-layers)
* [Tile/image display](#tileimage-display)
* [Tile load](#tile-load)
* [Vector tiles](#vector-tiles)


### Basemap providers

几乎不需要配置，开箱即用的底图。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/leaflet-extras/leaflet-providers">leaflet-providers</a>
		</td><td>
			包含各种免费 tile 提供程序的配置——OSM、OpenCycleMap、Stamen、Esri 等。
		</td><td>
			<a href="https://github.com/leaflet-extras">leaflet-extras members</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tontita/Leaflet.KoreanTmsProviders">Leaflet.KoreanTmsProviders</a>
		</td><td>
			包含各种（南）韩国瓦片（tile）供应商的配置——Daum、Naver、VWorld 等。
		</td><td>
			<a href="https://github.com/tontita/">Seong Choi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/htoooth/Leaflet.ChineseTmsProviders">Leaflet.ChineseTmsProviders</a>
		</td><td>
			包含各种中国瓦片（tile）供应商的配置——天地图、MapABC、高德等。
		</td><td>
			<a href="https://github.com/htoooth/">Tao Huang</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://esri.github.io/esri-leaflet">Esri Leaflet</a>
		</td><td>
			一组通过 Leaflet 使用 ArcGIS 服务的工具。支持地图服务、feature 图层、ArcGIS Online 切片等。
		</td><td>
			<a href="https://github.com/patrickarlt/">Patrick Arlt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/aparshin/leaflet-GIBS">Leaflet.GIBS</a>
		</td><td>
            <a href="https://earthdata.nasa.gov/gibs">NASA EOSDIS GIBS</a> 图像集成。该插件提供<a href="https://wiki.earthdata.nasa.gov/display/GIBS/GIBS+Available+Imagery+Products">96 个每日更新的图层</a>，其中包含卫星图像和科学参数。<a href="http://aparshin.github.io/leaflet-GIBS/examples/">Demo</a>。
		</td><td>
			<a href="https://github.com/aparshin">Alexander Parshin</a>
		</td>
	</tr>
        <tr>
		<td>
			<a href="https://github.com/knreise/L.TileLayer.Kartverket">L.TileLayer.Kartverket</a>
		</td><td>
            提供 <a href="http://kartverket.no/Kart/Gratis-kartdata/Cache-tjenester/">Kartverket</a>（挪威测绘局） 的瓦片（tile）图层的简单设置
		</td><td>
			<a href="https://github.com/knreise">Kultur og naturreise</a> / <a href="https://github.com/atlefren">Atle Frenvik Sveen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sigdeletras/Leaflet.Spain.WMS">Leaflet.Spain.WMS</a>
		</td><td>
            为西班牙制图机构提供的多个网络地图服务 (WMS) 图层（PNOA、IGN base、Catastro 等）提供简单的设置。
		</td><td>
			<a href="https://github.com/sigdeletras">Patricio Soriano</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/GeoSensorWebLab/polarmap.js">PolarMap.js</a>
		</td><td>
            用于显示来自 <a href="http://webmap.arcticconnect.org">ArcticWebMap</a> 的图块的 JavaScript 库，这是一个免费的图块提供程序，在多个北极极地投影中提供 OSM 数据。包括用于与其他 Leaflet 插件进行更深入集成的低级 API。
		</td><td>
			<a href="https://github.com/geosensorweblab">GeoSensorWeb Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gmaclennan/leaflet-bing-layer">Bing Maps Layer</a>
		</td><td>
            添加 <a href="https://msdn.microsoft.com/en-us/library/ff701721.aspx">Bing 地图的 tiles</a> 到你的 Leaflet 地图中， 需要 Leaflet v1.0.0.beta.2 或更高版本。
		</td><td>
			<a href="https://github.com/gmaclennan">Gregor MacLennan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.TileLayer.HERE">L.TileLayer.HERE</a>
		</td><td>
            显示来自 HERE 地图的地图 tiles(<a href="https://ivansanchez.gitlab.io/Leaflet.TileLayer.HERE/demo.html">demo</a>)。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.GridLayer.GoogleMutant">L.GridLayer.GoogleMutant</a>
		</td><td>
            显示谷歌地图(感谢 <a href='https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver'>DOM mutation observer</a> 方法，极大的减少了我的工作)(<a href="http://ivansanchez.gitlab.io/Leaflet.GridLayer.GoogleMutant/demo.html">demo</a>)。
			Displays Google maps (with minimal artifacts thanks to a <a href='https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver'>DOM mutation observer</a> technique) .
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.MapkitMutant">L.MapkitMutant</a>
		</td><td>
				显示 Apple 的 MapkitJS 底图。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>	</tr>
	<tr>
        <td>
        	<a href="https://supermap.github.io/supermap-leaflet">SuperMap Leaflet</a>
        </td><td>
         SuperMap Leaflet 是一个用于处理 SuperMap 服务类型的 Leaflet 插件。支持 SuperMap 服务、瓦片（tile）等。
        </td><td>
        	<a href="https://github.com/SuperMap">SuperMap</a>
        </td>
    </tr>
	<tr>
        <td>
        	<a href="https://github.com/MIERUNE/Leaflet.TileLayer.MIERUNE">Leaflet.TileLayer.Mierune</a>
        </td><td>
            显示 <a href="https://mierune.co.jp/tile.html">Mierune 地图</a> 中的瓦片（tile）。(<a href="https://tile.mierune.co.jp">Demo</a>)
        </td><td>
        	<a href="https://github.com/MIERUNE">Mierune</a>
        </td>
    </tr>
	<tr>
		<td>
			<a href="https://github.com/rkaravia/Leaflet.TileLayer.Swiss">Leaflet.TileLayer.Swiss</a>
		</td><td>
            使用来自 Swisstopo 地图中瑞士的国家地图的瓦片（tile）。 <a href="https://leaflet-tilelayer-swiss.karavia.ch/">Demo</a>。
		</td><td>
			<a href="https://github.com/rkaravia">Roman Karavia</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Azure-Samples/azure-maps-leaflet">Azure Maps Leaflet plugin</a>
		</td><td>
			一个 leafletjs 插件，可以轻松地叠加来自 <a href="https://azure.com/maps">Azure 地图</a>的所有不同瓦片图层。支持使用 Azure 地图订阅 key 或 Azure Active Directory 进行验证。 <a href="https://azuremapscodesamples.azurewebsites.net/?search=leaflet">Demos</a>。
		</td><td>
			<a href="https://github.com/rbrundritt">Ricky Brundritt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/wandersoncs/leaflet-tilelayer-here">Leaflet.TileLayer.HERE</a>
		</td><td>
			显示来自 HERE 地图的瓦片图层。
		</td><td>
			<a href="https://github.com/wandersoncs">Wanderson Souza</a>
		</td>
	</tr>
</table>



### Basemap formats

以下插件用于加载常见格式（非默认）的底图或者栅格图层。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/mylen/leaflet.TileLayer.WMTS">leaflet.TileLayer.WMTS</a>
		</td><td>为 Leaflet 添加 WMTS (IGN) 图层。
		</td><td>
			<a href="https://github.com/mylen">Alexandre Melard</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/azgs/azgs-leaflet">azgs-leaflet</a>
		</td><td>
			Leaflet 的一组小插件，包括带过滤的 WFS-GeoJSON 层、GeoJSON 的悬停控件和 Esri 平铺层。
		</td><td>
			<a href="https://github.com/azgs">AZGS</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/heigeo/leaflet.wms">leaflet.wms</a>
		</td><td>
			增强了对 Leaflet 的 WMS 支持，包括 single-tile/untiled 图层、共享 WMS 源以及通过 GetFeatureInfo 进行的图层识别。
		</td><td>
			<a href="https://github.com/sheppard/">S. Andrew Sheppard</a><br>(<a href="https://github.com/heigeo/">HEI Geo</a>)
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/alcalin/L.TileLayer.WMTS">L.TileLayer.WMTS</a>
		</td><td>
			一个简单的用于Leaflet 的 WMTS 瓦片（tile）图层插件。
		</td><td>
			<a href="https://github.com/alcalin">Alexandru Calin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stuartmatthews/Leaflet.NonTiledLayer.WCS">Leaflet.NonTiledLayer.WCS</a>
		</td><td>
            显示来自 Web Coverage Services 的栅格数据。可以在客户端对栅格进行样式设置和查询。查看<a href="https://stuartmatthews.github.io/Leaflet.NonTiledLayer.WCS/">demo</a>。
		</td><td>
			<a href="https://github.com/stuartmatthews">Stuart Matthews</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/balrog-kun/Leaflet.bpg">Leaflet.bpg</a>
		</td><td>
            TileLayer 和 <a href="http://bellard.org/bpg/">.bpg</a> 图像格式的解码。
		</td><td>
			<a href="https://github.com/balrog-kun/">Andrzej Zaborowski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/glenrobertson/leaflet-tilelayer-geojson/">TileLayer.GeoJSON</a>
		</td><td>
			用于 GeoJSON 切片的 TileLayer。
		</td><td>
			<a href="https://github.com/glenrobertson">Glen Robertson</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/kartena/leaflet-tilejson">leaflet-tilejson</a>
		</td><td>
            添加了 TileJSON 规范说明文档。
			Adds support for the <a href="https://github.com/mapbox/TileJSON">TileJSON</a> specification to Leaflet.
		</td><td>
			<a href="https://github.com/perliedman">Per Liedman</a>, <a href="http://www.kartena.se/">Kartena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://vizzuality.github.com/cartodb-leaflet/">cartodb-leaflet</a>
		</td><td>
            Leaflet 的官方 CartoDB 插件。
		</td><td>
			<a href="http://vizzuality.com/">Vizzuality</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/emikhalev/leaflet-2gis">Leaflet-2gis</a>
		</td><td>
			添加对 2GIS 切片图层的支持
		</td><td>
			<a href="https://github.com/emikhalev/">Eugene Mikhalev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/geobricks/Leaflet.GeoJSON.Encoded">Leaflet GeoJSON Encoded</a>
		</td><td>
            使用 Google 折线编码算法扩展 L.GeoJSON 层，允许优化数据传输。
		</td><td>
			<a href="https://github.com/geobricks/">Geobricks</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.TileLayer.MBTiles">Leaflet.TileLayer.MBTiles</a>
		</td><td>
			加载 <a href="https://github.com/mapbox/mbtiles-spec"><code>.mbtiles</code></a> .
		</td><td>
			<a href="https://github.com/IvanSanchez/">Iván Sánchez</a>
		</td>
	</tr>
    <tr>
		<td>
			<a href="https://github.com/IHCantabria/Leaflet.CanvasLayer.Field">Leaflet.CanvasLayer.Field</a>
		</td><td>
            加载和样式光栅文件（geotiff 和 asciigrid 格式）。它包括一个 ScalarField 层（用于 DTM、温度...）和 VectorFieldAnim（用于风、流...的动画层）。查看<a href="https://ihcantabria.github.io/Leaflet.CanvasLayer.Field/">示例</a>
		</td><td>
			<a href="https://github.com/VictorVelarde">Víctor Velarde</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stuartmatthews/leaflet-geotiff">leaflet-geotiff</a>
		</td><td>
            将 geoTIFF 文件中的栅格数据显示为图像或方向箭头。可以在客户端对栅格进行样式设置和查询。可以应用可选的剪切蒙版，例如将 DEM 限制为陆地区域。请参阅<a href="https://stuartmatthews.github.io/leaflet-geotiff/">demo</a>。
		</td><td>
			<a href="https://github.com/stuartmatthews">Stuart Matthews</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/geotiff/georaster-layer-for-leaflet">GeoRasterLayer</a>
		</td><td>
			以可配置的分辨率显示小型和大型 GeoTIFF 文件。 简单并且具有高性能。 这是一个 JavaScript 光栅分析库, 集成了 <a href="https://geoblaze.io/">GeoBlaze</a> 。 请参见 <a href="https://geotiff.github.io/georaster-layer-for-leaflet-example/">Demo</a>。
		</td><td>
			<a href="https://github.com/DanielJDufour">Daniel J. Dufour</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/GeoportalPL/leaflet.projwmts">Leaflet.projwmts</a>
		</td><td>
			添加 WMTS 服务 (GUGiK Poland)。
		 (<a href="https://geoportalpl.github.io/leaflet.projwmts/examples/wmts_services.html">demo</a>).
		</td><td>
			<a href="https://github.com/GeoportalPL">Geoportal Poland</a>
		</td>
	</tr>
</table>


### Non-map base layers

有时候你不想加载地图，只想加载大的自定义图像，**非常大**的那种。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/cmulders/Leaflet.Zoomify">TileLayer.Zoomify</a>
		</td><td>
			用于缩放图像的 TileLayer。
		</td><td>
			<a href="https://github.com/turban">Bjørn Sandvik</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/alfarisi/leaflet-deepzoom">TileLayer.DeepZoom</a>
		</td><td>
			用于DeepZoom图像的TileLayer。
		</td><td>
			<a href="https://github.com/alfarisi">Al Farisi</a>,
			<a href="http://indokreatif.net">Indokreatif Teknologi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/namrehs/Leaflet.Gigapan">TileLayer.Gigapan</a>
		</td><td>
			用于 Gigapan 图像的 TileLayer。
		</td><td>
			<a href="https://github.com/namrehs">Dan Sherman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/astromatic/Leaflet.TileLayer.IIP">Leaflet.TileLayer.IIP</a>
		</td><td>在 Leaflet 中添加对 <a href="http://iipimage.sourceforge.net/">IIPImage</a>  层的支持。
		</td><td>
			<a href="https://github.com/ebertin">Emmanuel Bertin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mejackreed/Leaflet-IIIF">Leaflet-IIIF</a>
		</td><td>
            一个 Leaflet的 IIIF（国际形象互操作性框架）查看器。查看  <a href="http://mejackreed.github.io/Leaflet-IIIF/examples/example.html">demo</a>。
		</td><td>
			<a href="https://github.com/mejackreed">Jack Reed</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/aparshin/leaflet-fractal">leaflet-fractal</a>
		</td><td>
            使用2D画布渲染一些分形（Mandelbrot集、Julia集和其他的）(<a href="http://aparshin.github.io/leaflet-fractal/">demo</a>)。
		</td><td>
			<a href="https://github.com/aparshin">Alexander Parshin</a>
		</td>
	</tr>
	<tr>
	  <td>
	    <a href="https://github.com/commenthol/leaflet-rastercoords">leaflet-rastercoords</a>
	  </td><td>
        渲染使用 <a href="http://github.com/commenthol/gdal2tiles-leaflet">gdal2tiles-leaflet</a> 生成的大型平铺图像 。图像光栅坐标可用于设置标记等(<a href="http://commenthol.github.io/leaflet-rastercoords">demo</a>)。
	  </td><td>
	    <a href="https://github.com/commenthol">Commenthol</a>
	  </td>
	</tr>
</table>



### Tile/image display

以下插件更改了地图中显示瓦片（tile）或图像(image)图层的方式。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/aparshin/leaflet-boundary-canvas">TileLayer.BoundaryCanvas</a>
		</td><td>
			允许您绘制具有任意多边形边界的切片图层并使用HTML5 Canvas 来渲染。
		</td><td>
			<a href="https://github.com/aparshin">Alexander Parshin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Zverik/leaflet-grayscale/">TileLayer.Grayscale</a>
		</td><td>
			具有灰度改造（grayscale makeover）的常规 TileLayer。
		</td><td>
			<a href="https://github.com/Zverik">Ilya Zverev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ScanEx/Leaflet.imageTransform">Leaflet.ImageTransform</a>
		</td><td>支持对具有任意透视变换的图像进行叠加。
		</td><td>
			<a href="https://github.com/aparshin">Alexander Parshin</a>,
			<a href="https://github.com/OriginalSin">Sergey Alekseev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/lizardtechblog/Leaflet.OpacityControls">Leaflet.OpacityControls</a>
		</td><td>
			简单的、可调整地图图层的不透明度的 Leaflet 控件。
		</td><td>
			<a href="https://github.com/lizardtechblog/">Jared Dominguez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/publiclab/Leaflet.DistortableImage">Leaflet.DistortableImage</a>
		</td><td>
            使用户能够在 Leaflet 地图上<a href="https://publiclab.github.io/Leaflet.DistortableImage/examples/">缩放、旋转和扭曲(distort)图像</a>。
		</td><td>
			<a href="https://github.com/publiclab">Public Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ronikar/Leaflet.DistortableVideo">Leaflet.DistortableVideo</a>
		</td><td>
			使用户能够在 Leaflet 地图上缩放、旋转和扭曲(distort)视频(<a href='https://ronikar.github.io/Leaflet.DistortableVideo/examples/'>demo</a>)。
		</td><td>
			<a href="https://github.com/ronikar">Roni Karilkar</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.ImageOverlay.Rotated">Leaflet.ImageOverlay.Rotate</a>
		</td><td>
            在给定三个控制点的情况下，显示旋转、缩放和倾斜（但不是 rubbersheeted）的 ImageOverlays(<a href='http://ivansanchez.github.io/Leaflet.ImageOverlay.Rotated/demo.html'>demo</a>)。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.ImageOverlay.Arrugator">Leaflet.ImageOverlay.Arrugator</a>
		</td><td>
            给定四个控制点和一个 proj4js 投影函数，显示重新投影的 ImageOverlays(<a href='https://ivansanchez.gitlab.io/Leaflet.ImageOverlay.Arrugator/demo.html'>demo</a>)。
		</td><td>
			<a href="https://ivan.sanchezortega.es">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/xtk93x/Leaflet.TileLayer.ColorFilter">Leaflet.TileLayer.ColorFilter</a>
		</td><td>
            一个简单而轻量级的 Leaflet 插件，用于在地图瓦片（tile）上应用 CSS 过滤器(<a href="https://xtk93x.github.io/Leaflet.TileLayer.ColorFilter/">demo</a>)。
		</td><td>
			<a href="https://github.com/xtk93x">Cláudio Kawakani</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/frogcat/leaflet-tilelayer-mask">Leaflet.TileLayer.Mask</a>
		</td><td>
            带有遮罩效果的 TileLayer (<a href="http://frogcat.github.io/leaflet-tilelayer-mask/default/">demo</a>)。
		</td><td>
			<a href="https://github.com/frogcat">Yuzo Matsuzawa</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/GreenInfo-Network/L.TileLayer.PixelFilter/">Leaflet.TileLayer.PixelFilter</a>
		</td><td>
            可以通过 RGB 代码过滤和替换像素的 TileLayer。
			<br/>
			<a href="http://greeninfo-network.github.io/L.TileLayer.PixelFilter/demo1.html">demo 1</a> &bull; <a href="http://greeninfo-network.github.io/L.TileLayer.PixelFilter/demo2.html">demo 2</a>
		</td><td>
			<a href="https://github.com/GreenInfo-Network/">GreenInfo Network</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/digidem/leaflet-side-by-side">Leaflet.Control.SideBySide</a>
		</td><td>
            一个用于添加分屏以比较两个地图叠加层的 Leaflet 控件，（<a href="http://lab.digital-democracy.org/leaflet-side-by-side/">demo</a>）。
		</td><td>
			<a href="http://www.digital-democracy.org">Digital Democracy</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.TileLayer.GL">Leaflet.TileLayer.GL</a>
		</td><td>
            将自定义 WebGL 着色器应用于 tilelayer 中的每个图块（<a href="https://ivansanchez.gitlab.io/Leaflet.TileLayer.GL/demo/repl.html">demo</a>）。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/frogcat/leaflet-tilelayer-colorpicker">Leaflet.TileLayer.ColorPicker</a>
		</td><td>
            带有 getColor(latLng) 的 Leaflet TileLayer。Demos: <a href="https://frogcat.github.io/leaflet-tilelayer-colorpicker/">颜色选择器</a>, <a href="https://frogcat.github.io/leaflet-tilelayer-colorpicker/mapbox-terrain-rgb.html">带有 mapbox terrain-RGB 的高程选择器</a>
		</td><td>
			<a href="https://github.com/frogcat">Yuzo Matsuzawa</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/hnrchrdl/leaflet-tilelayer-colorizr">Leaflet.TileLayer.Colorizr</a>
		</td><td>
			一个可以通过 RGBA 代码修改颜色的 Leaflet TileLayer。Demo：即将推出。
		</td><td>
			<a href="https://github.com/hnrchrdl">Hinrich Riedel</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/consbio/Leaflet.UTFGrid">Leaflet.UTFGrid</a>
		</td><td>
			为 Leaflet >= 1.0 提供 UTF-8 网格支持。包括基本的鼠标悬停支持以及在悬停时突出显示 UTFGrid 功能的能力 (<a href="https://consbio.github.io/Leaflet.UTFGrid/">demo</a>).
		</td><td>
			<a href="https://github.com/brendan-ward">Brendan Ward</a>
		</td>
	</tr>
	<tr>
        	<td>
        		<a href="https://github.com/dayjournal/Leaflet.Control.Opacity">Leaflet.Control.Opacity</a>
        	</td><td>
			使多个瓦片（tile）图层透明。(<a href="https://dayjournal.github.io/Leaflet.Control.Opacity">demo</a>)
        	</td><td>
        		<a href="https://day-journal.com">Yasunori Kirimoto</a>
        	</td>
    	</tr>
	<tr>
		<td>
			<a href="https://github.com/ihmeuw/leaflet.tilelayer.glcolorscale">Leaflet.TileLayer.GLColorScale</a>
		</td><td>
			TileLayer 使用 WebGL 根据指定的色标对浮点像素进行着色 (<a href="https://ihmeuw.github.io/leaflet.tilelayer.glcolorscale/demo/">demo</a>)。
		</td><td>
			<a href="https://github.com/davschne">David Schneider</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/valkenburg/Leaflet.Control.DetailLevel">Leaflet.Control.DetailLevel</a>
		</td><td>
			通过实时修改 zoomOffset 以高于视网膜 (hdpi) 的分辨率显示图块。对于在不同缩放级别之间彻底改变地图样式的映射源很有用。将 zoomOffset 增加太多确实会减慢浏览器的速度，因为显示的图块数量随着 zoomOffset 呈指数增长。 (<a href='https://valkenburg.github.io/Leaflet.Control.DetailLevel/demo.html'>demo</a>)
		</td><td>
			<a href="https://github.com/valkenburg">Wessel Valkenburg</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/publiclab/leaflet-multispectral">Leaflet.Multispectral</a>
		</td><td>
			使用纯客户端 JavaScript 为 Leaflet 图像层提供多光谱通道操作和处理工具（例如 NDVI 或其他遥感方法）。它通过 ImageOverlay `filter()` 函数使用 `image-sequencer`。 (<a href='https://publiclab.github.io/leaflet-multispectral/'>demo</a>)
		</td><td>
			<a href="https://publiclab.org">Public Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/equinor/leaflet.tilelayer.gloperations">Leaflet.TileLayer.GLOperations</a>
		</td><td>
			WebGL TileLayer：着色浮点像素、像素值的鼠标事件处理程序、山体阴影、轮廓、过渡、过滤和在多个图层上进行计算。(<a href="https://equinor.github.io/leaflet.tilelayer.gloperations/">Demo</a>)
		</td><td>
			<a href="https://github.com/thor85">Thorbjørn Horgen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ptv-logistics/Leaflet.NonTiledLayer">Leaflet.NonTiledLayers</a>
		</td><td>
			一个用于 non-tiled overlays 的 Leaflet 图层。
			 (<a href="https://ptv-logistics.github.io/Leaflet.NonTiledLayer/index.html">Demo</a>)
		</td><td>
			<a href="https://github.com/ptv-logistics">PTV Logistics</a>
		</td>
	</tr>
</table>



### Tile load

下面插件改变了将瓦片（Tile）图层加载到地图中的方式。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/mattiasb/Leaflet.MultiTileLayer">Leaflet.MultiTileLayer</a>
		</td><td>
			允许将多个瓦片（tile）数据源组成一个 TileLayer。每个源仅在定义的一组缩放级别上处于活动状态。
		</td><td>
			<a href="https://github.com/mattiasb">Mattias Bengtsson</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ismyrnow/Leaflet.functionaltilelayer">Leaflet.FunctionalTileLayer</a>
		</td><td>
			允许您使用函数定义瓦片（Tile）图层 URL。甚至可以使用 Promise 来处理异步源。
		</td><td>
			<a href="https://github.com/ismyrnow">Ishmael Smyrnow</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gregallensworth/L.TileLayer.Cordova">TileLayer.Cordova</a>
		</td><td>
			与 Cordova/Phonegap 一起使用，将瓦片（Tile）缓存添加到本地设备存储，在离线和在线模式之间切换。
		</td><td>
			<a href="https://github.com/gregallensworth">Greg Allensworth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MazeMap/Leaflet.TileLayer.PouchDBCached">TileLayer.PouchDBCached</a>
		</td><td>
			允许所有 Leaflet TileLayers 缓存到 PouchDB 以供离线使用。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ebrelsford/Leaflet.loading">Leaflet.loading</a>
		</td><td>
			一个简单的控件，在加载瓦片（Tile）和其他数据时添加加载指示器。
		</td><td>
			<a href="https://github.com/ebrelsford/">Eric Brelsford</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/TolonUK/Leaflet.EdgeBuffer">Leaflet.EdgeBuffer</a>
		</td><td>
			超出视口边缘的缓冲平铺，用于 Leaflet 1.0。 <a href="http://www.tolon.co.uk/Leaflet.EdgeBuffer/comparison.html">Demo</a>
		</td><td>
			<a href="https://github.com/TolonUK">Alex Paterson</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ghybs/Leaflet.TileLayer.Fallback">Leaflet.TileLayer.Fallback</a>
		</td><td>
			通过从较低的缩放比例放大等效的瓦片（Tile）来替换丢失的瓦片（Tile）（HTTP 404 未找到错误）。
		</td><td>
			<a href="https://github.com/ghybs">ghybs</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Outdooractive/Leaflet.FeatureGroup.LoadEvents">Leaflet.FeatureGroup.LoadEvents</a>
		</td><td>
			`FeatureGroup` 支持 `"loading"` 和 `"load"` 事件（适用于 v0.7.*）。
		</td><td>
			<a href="http://glat.info">G. Lathoud</a>, <a href="http://www.outdooractive.com">Outdooractive</a>.
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.GridLayer.FadeOut">Leaflet.GridLayer.FadeOut</a>
		</td><td>
			删除网格层和 tilelayers 时淡出它们，使底图更改更平滑（对于 1.0.0） <a href="http://ivansanchez.gitlab.io/Leaflet.GridLayer.FadeOut/demo.html">Demo</a>
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/robertomlsoares/leaflet-offline">leaflet-offline</a>
		</td><td>
			允许以可自定义的方式使用离线瓦片（tile）数据，同时在必要时回退到正常的 TileLayer。 <a href="https://robertomlsoares.github.io/leaflet-offline/">Demo</a>
		</td><td>
			<a href="https://github.com/robertomlsoares">Roberto Soares</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/allartk/leaflet.offline">leaflet.offline</a>
		</td><td>
			允许将瓦片（Tile）存储在数据库中以供离线访问。原创插件。<a href="http://allartk.github.io/leaflet.offline/">Demo</a>
		</td><td>
			<a href="https://github.com/allartk">Allart Kooiman</a>
		</td>
	</tr>
</table>



### Vector tiles

用来显示[矢量瓦片（Tile）](https://github.com/mapbox/vector-tile-spec) 的插件。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/SpatialServer/Leaflet.MapboxVectorTile">Leaflet.MapboxVectorTile</a>
		</td><td>
			在画布上渲染 Mapbox 矢量瓦片（Tile）的 Leaflet 插件。见 <a href="http://spatialserver.github.io/Leaflet.MapboxVectorTile/examples/confetti.html">demo</a>。仅与 Leaflet 0.7.x 兼容。
		</td><td>
			<a href="http://spatialdev.com/">SpatialDev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/devTristan/hoverboard">Hoverboard</a>
		</td><td>
			使用 Leaflet（geojson、topojson 和 protobuf）在画布上渲染矢量瓦片（Tile）。见 <a href="http://tristan.io/hoverboard/">demo</a>。 仅与 Leaflet 0.7.x 兼容。
		</td><td>
			<a href="http://tristan.io/">Tristan Davies</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iamtekson/leaflet-geojson-vt">leaflet-geojson-vt</a>
		</td><td>
			Displaying the vector tiles of GeoJSON data on the fly on leaflet
		</td><td>
			<a href="https://github.com/iamtekson">Tek Kshetri</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapbox/geojson-vt">geojson-vt</a>
		</td><td>
			用于将 GeoJSON 数据动态瓦片（Tile）转换为矢量瓦片（Tile）的高效库。
		</td><td>
			<a href="https://www.mapbox.com/">Mapbox</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.VectorGrid">Leaflet.VectorGrid</a>
		</td><td>
			在 Leaflet 1.0.0 中显示网格矢量数据（用 geojson-vt 或 protobuf 矢量瓦片（Tile）的 GeoJSON 或 TopoJSON）。见 <a href="https://github.com/IvanSanchez/Leaflet.VectorGrid#demos">demos</a>。  与 Leaflet 0.7.x 不兼容。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/jkuebart/Leaflet.VectorTileLayer/">Leaflet.VectorTileLayer</a>
		</td><td>
            用于显示矢量切片的传单层。除了样式之外，与 <a href="https://github.com/IvanSanchez/Leaflet.VectorGrid">Leaflet.VectorGrid</a> 非常相似：可以为所有图层指定一个样式，而 VectorGrid 需要提前知道图层名称。支持 Leaflet 1.0.0。
		</td><td>
			<a href="https://gitlab.com/jkuebart/">Joachim Kuebart</a>
		</td>
	</tr>
</table>


## 叠加数据

以下插件提供了加载叠加数据（GIS 矢量数据）的新方法：点、线和多边形。

* [叠加数据格式](#overlay-data-formats)
* [动态加载数据](#dynamiccustom-data-loading)
* [合成叠加的数据](#synthetic-overlays)
* [数据提供程序](#data-providers)

### Overlay data formats

使用各种 GIS 格式加载您自己的数据。

<table class="plugins"><tr><th>插件</th><th>描述</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/windycom/leaflet-kml">leaflet-kml</a>
		</td><td>
			加载和显示 KML
		</td><td>
			<a href="https://github.com/windycom">Windyx</a>
		</td>
	</tr>
    <tr>
		<td>
			<a href="https://github.com/mapbox/leaflet-omnivore">leaflet-omnivore</a>
		</td><td>
			为 Leaflet 加载和转换 CSV、KML、GPX、TopoJSON、WKT 格式。
		</td><td>
			<a href="https://github.com/mapbox">Mapbox</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.FileLayer">Leaflet.FileLayer</a>
		</td><td>
			使用 HTML5 FileReader API（即本地无服务器）将文件（GeoJSON、GPX、KML）加载到地图中。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/joker-x/Leaflet.geoCSV">Leaflet.geoCSV</a>
		</td><td>
			用于将 CSV 文件加载为 geoJSON 图层的 Leaflet 插件。
		</td><td>
			<a href="https://github.com/joker-x">Iván Eixarch</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/calvinmetcalf/leaflet.shapefile">Leaflet.Shapefile</a>
		</td><td>
			将 shapefile 作为图层放在地图上。
		</td><td>
			<a href="https://github.com/calvinmetcalf">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/calvinmetcalf/leaflet.filegdb">Leaflet.FileGDB</a>
		</td><td>
			将 ESRI 文件地理数据库作为图层放在地图上。
		</td><td>
			<a href="https://github.com/calvinmetcalf">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jieter/Leaflet.encoded">Leaflet.encoded</a>
		</td><td>
			在 Leaflet 中使用编码的折线。
		</td><td>
			<a href="https://github.com/jieter">Jieter</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mpetazzoni/leaflet-gpx">Leaflet GPX</a>
		</td><td>
			GPX 层，通过提供对距离、移动时间、配速、海拔、心率等信息的访问，针对体育活动。
		</td><td>
			<a href="https://github.com/mpetazzoni/">Maxime Petazzoni</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://arthur-e.github.com/Wicket/">Wicket</a>
		</td><td>
            用于在众所周知的文本 (WKT) 和 Leaflet 几何对象（例如，在 L.marker() 实例和“POINT()”字符串之间）之间进行翻译的适度库。
		</td><td>
			<a href="https://github.com/arthur-e/">K. Arthur Endsley</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tomchadwin/qgis2web">qgis2web</a>
		</td><td>
            一个使用 webmaps 无需编码的 <a href="http://qgis.org/">QGIS</a> 插件。
		</td><td>
			<a href="https://github.com/tomchadwin">Tom Chadwin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Flexberry/Leaflet-WFST">Leaflet-WFST</a>
		</td><td>
            支持事务的 <a href="http://www.opengeospatial.org/standards/wfs">WFS</a> 客户端层。
		</td><td>
			<a href="https://github.com/Flexberry/">Flexberry</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/daniellsu/leaflet-betterscale">Leaflet-BetterScale</a>
		</td><td>
			一个新的、带有交替的黑/白条、更像 GIS 的比例尺。
		</td><td>
			<a href="https://github.com/daniellsu/">Dan Brown</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ngageoint/geopackage-js/tree/master/leaflet">Leaflet-GeoPackage</a>
		</td><td>
			加载 <a href="http://www.geopackage.org/">GeoPackage</a> 瓦片（Tile） and 要素（Feature）图层。
		</td><td>
			<a href="https://github.com/danielbarela">Daniel Barela</a>,
			<a href="https://github.com/ngageoint">NGA</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gherardovarando/leaflet-csvtiles">Leaflet-CsvTiles</a>
		</td><td>
        使用令人惊叹的 <a href="http://papaparse.com/">PapaParse</a> 库从瓦片（Tile）的 csv 文件中加载数据。<a href="https://gherardovarando.github.io/leaflet-csvtiles/demo/index.html">Demo</a>。
		</td><td>
			<a href="https://github.com/gherardovarando">Gherardo Varando</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-layerJSON">Leaflet LayerJSON</a>
		</td><td>
		Simple way for transform any JSON data source in a Leaflet Layer, load JSON data in layer and minimize remote requests with caching system <a href="https://opengeo.tech/maps/leaflet-layerjson/">Demo</a>.
		</td><td>
			<a href="https://opengeo.tech/">Stefano Cudini</a>
		</td>
	</tr>	
</table>



### Dynamic/custom data loading

加载地图中更新的动态数据，或以非标准方式加载GIS矢量数据。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/ATran31/Leaflet-GeoSSE">Leaflet GeoSSE</a>
		</td><td>
			Add realtime data to a Leaflet map using server sent events.
		</td><td>
			<a href="https://github.com/ATran31/">An Tran</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/perliedman/leaflet-realtime">Leaflet Realtime</a>
		</td><td>
			将实时数据放在 Leaflet 地图上：实时跟踪 GPS 单元、传感器数据或任何东西。
		</td><td>
			<a href="https://github.com/perliedman/">Per Liedman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/calvinmetcalf/leaflet-ajax">Leaflet Ajax</a>
		</td><td>
			通过 ajax 或 jsonp 添加 GeoJSON 数据。
		</td><td>
			<a href="https://github.com/calvinmetcalf/">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tinuzz/leaflet-liveupdate">Leaflet.Liveupdate</a>
		</td>
		<td>
			定期（“实时”）更新地图上的某些内容 (<a href="https://www.grendelman.net/leaflet/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/tinuzz/">Martijn Grendelman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/calvinmetcalf/leaflet.pouch">Leaflet.Pouch</a>
		</td><td>
			使用 PouchDB 将 CouchDB 数据同步到本地存储（indexedDB），只添加 couchDB 数据或作为 indexedDB 的一个不那么混乱的实现。
		</td><td>
			<a href="https://github.com/calvinmetcalf/">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/cbaines/leaflet-indoor">Leaflet.Indoor</a>
		</td><td>
			创建室内地图。
		</td><td>
			<a href="https://github.com/cbaines">Christopher Baines</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/BenjaminVadant/leaflet-ugeojson">Leaflet uGeoJSON</a>
		</td><td>
			通过 ajax post 请求添加自动更新 GeoJSON 数据层。
		</td><td>
			<a href="https://github.com/BenjaminVadant/">Benjamin VADANT</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dj0001/Leaflet.mytrack">Leaflet.mytrack</a>
		</td><td>在地图上追踪我的路线并下载。<a href="https://dj0001.github.io/Leaflet.mytrack">Demo</a>
		</td><td>
			<a href="https://github.com/dj0001">DJ</a>
		</td>
	</tr>
</table>



### Synthetic overlays

这些插件从头开始创建有用的叠加层，无需加载。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/turban/Leaflet.Graticule">Leaflet.Graticule</a>
		</td><td>
			绘制经纬度网格线。
		</td><td>
			<a href="https://github.com/turban">Bjørn Sandvik</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ablakey/Leaflet.SimpleGraticule">Leaflet.SimpleGraticule</a>
		</td><td>
			为 L.CRS.Simple 坐标系绘制网格线。
		</td><td>
			<a href="https://github.com/ablakey">Andrew Blakey</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jonshutt/Leaflet.OS.Graticule">L.OS.Graticule</a>
		</td><td>
			覆盖 UK Ordinance Survey (OS) 1km 栅格和标签。
		</td><td>
			<a href="https://github.com/jonshutt">Jon Shutt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bill-chadwick/Leaflet.MetricGrid">Leaflet.MetricGrid</a>
		</td><td>
			具有现成定义的 UTM、英国和爱尔兰网格的 Leaflet 的通用度量网格覆盖。
		</td><td>
			<a href="https://github.com/bill-chadwick">Bill Chadwick</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/joergdietrich/Leaflet.Terminator">Leaflet.Terminator</a>
		</td><td>在地图上叠加昼夜区域。
		</td><td>
			<a href="https://github.com/joergdietrich">J&ouml;rg Dietrich</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dj0001/Leaflet.Sun">Leaflet.Sun</a>
		</td><td>点击地图获取日落或日出。 <a href="https://dj0001.github.io/Leaflet.Sun">Demo</a>
		</td><td>
			<a href="https://github.com/dj0001">DJ</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dj0001/Leaflet.timezones">Leaflet.timezones</a>
		</td><td>在 Leaflet 地图上叠加时区。 <a href="https://dj0001.github.io/Leaflet.timezones">Demo</a>
		</td><td>
			<a href="https://github.com/dj0001">DJ</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/cloudybay/leaflet.latlng-graticule">leaflet.latlng-graticule</a>
		</td>
		<td>
        创建一个 Canvas 作为 ImageOverlay 来绘制 Lat/Lon Graticule，并在地图的边缘显示网格刻度标签。<a href="https://cloudybay.github.io/leaflet.latlng-graticule/example/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/cloudybay/">CloudyBay</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://github.com/GEOF-OSGL/Leaflet.EdgeScaleBar">Leaflet.EdgeScaleBar</a>
		</td>
		<td>
			在 Web Mercator 投影中沿地图的顶部和右侧边缘创建比例尺。<a href="http://geof-osgl.github.io/Leaflet.EdgeScaleBar/">Demo</a>
		</td>
		<td>
			<a href="http://github.com/GEOF-OSGL">Dražen Tutić, Ana Kuveždić Divjak</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/leaflet.maidenhead">Leaflet.Maidenhead</a>
		</td><td>
			实现一个 <a href="https://en.wikipedia.org/wiki/Maidenhead_Locator_System">Maidenhead 定位系统网格服务</a> <a href="https://ivansanchez.gitlab.io/leaflet.maidenhead/demo.html">Demo</a>
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/facilmap/Leaflet.AutoGraticule">Leaflet.AutoGraticule</a>
		</td><td>
			Draws a grid of latitude and longitude lines, automatically adjusting the scale to the current zoom level. <a href="https://unpkg.com/leaflet-auto-graticule/example.html">Demo</a>
		</td><td>
			<a href="https://github.com/cdauth">Candid Dauth</a>
		</td>
	</tr>
</table>



### Data providers

从三方服务加载叠加数据。 另请参阅 [Basemap providers](#basemap-providers) 和 [插件合计](#collections).

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="http://jasonsanford.github.io/leaflet-vector-layers/">Leaflet Vector Layers</a>
		</td><td>
			允许从许多地理网络服务轻松创建矢量图层，例如 ArcGIS Server、Arc2Earth、GeoIQ、CartoDB 和 GIS Cloud。
		</td><td>
			<a href="http://geojason.info">Jason Sanford</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/GuillaumeAmat/leaflet-overpass-layer">Leaflet Overpass Layer</a>
		</td><td>
        轻松集成来自 <a href="http://overpass-api.de">overpass api</a> 的数据。 
		</td><td>
			<a href="https://github.com/GuillaumeAmat">Guillaume AMAT</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/kr1/Leaflet.dbpediaLayer/">Leaflet.dbpediaLayer</a>
		</td><td>
			一个包含维基百科兴趣点的层--通过ajax从DBpedia的SPARQL端点加载。
		</td><td>
			<a href="https://github.com/kr1/">Kr1</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MatthewBarker/leaflet-wikipedia">Leaflet-Wikipedia</a>
		</td>
		<td>
			一个用于在地图层上显示 Wikipedia API 条目的 Leaflet 插件。
		</td>
		<td>
			<a href="https://github.com/MatthewBarker">Matthew Barker</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/windycom/API">Windy-Leaflet-plugin</a>
		</td>
		<td>
			使用 Windy 的免费 API 在您的页面上显示动画天气图。
		</td>
		<td>
			<a href="https://www.windy.com">Windy.com</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/barryhunter/Leaflet.GeographPhotos">Leaflet.GeographPhotos</a>
		</td>
		<td>
			使用他们的 API 在交互式叠加中显示来自 Geograph British and Ireland 的地理照片。
		</td>
		<td>
			<a href="https://github.com/barryhunter/">Barry Hunter</a>
		</td>
	</tr>
        <tr>
                <td>
  		<a href="https://github.com/rwev/leaflet-radar">leaflet-radar</a>
		</td>
		<td>
            Leaflet 的动画卫星天气雷达覆盖图。
		</td>
		<td>
			<a href="https://github.com/rwev/">rwev</a>
                </td>
        </tr>
	<tr>
		<td>
			<a href="https://github.com/publiclab/leaflet-environmental-layers">leaflet-environmental-layers
			</a>
		</td>
		<td>
			在一个易于使用的 Leaflet 库中收集不同的环境地图图层 <a href="https://publiclab.github.io/leaflet-environmental-layers/example/index.html#3/43.00/-46.26/BL2">Demo</a>
		</td>
		<td>
			<a href="https://github.com/publiclab">Public Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mwasil/Leaflet.Rainviewer">Leaflet.Rainviewer
			</a>
		</td>
		<td>
			RainViewer雷达数据API插件 <a href="https://mwasil.github.io/Leaflet.Rainviewer/demo/">Demo</a>.
		</td>
		<td>
			<a href="https://marcinwasilewski.eu/">Marcin Wasilewski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/facilmap/Leaflet.FreieTonne">Leaflet.FreieTonne</a>
		</td><td>
			An overlay with nautical features from <a href="https://www.freietonne.de/">FreieTonne</a>. (<a href="https://unpkg.com/leaflet-freie-tonne/example.html">Demo</a>)
		</td><td>
			<a href="https://github.com/cdauth">Candid Dauth</a>
		</td>
	</tr>
</table>



## 叠加显示

以下插件提供了显示叠加数据信息的新方法。

* [标记 & 渲染](#markers--renderers)
* [叠加动画](#overlay-animations)
* [Clustering/decluttering](#clusteringdecluttering)
* [热力图](#heatmaps)
* [数据可视化](#dataviz)


### Markers & renderers

这些插件提供了将抽象数据转换为屏幕中图像的新的标记（marker）或路径（way），精通 GIS 的 Leaflet 用户也将这些称为符号。

<table class="plugins"><tr><th>插件</th><th>说明</th><th>维护者</th></tr>
	<tr>
		<td>
			<a href="https://github.com/damianc/leaflet-place-groups-picker">leaflet-place-groups-picker</a>
		</td><td>
			Plugin for the Leaflet maps that allows grouping places in groups whose visibility can be toggled.
		</td><td>
			<a href="https://github.com/damianc">damianc</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/zhuang-hao-ming/Leaflet.RoughCanvas">Leaflet.RoughCanvas</a>
		</td><td>
            Leaflet.RoughCanvas 渲染手绘、草图风格的矢量图（折线、多边形、geojson）。
		</td><td>
			<a href="https://github.com/zhuang-hao-ming/">haoming</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jdfergason/Leaflet.Ellipse">Leaflet.ellipse</a>
		</td><td>
            Leaflet.ellipse 通过指定中心点、长半轴、短半轴和向西倾斜度在地图上放置椭圆。
		</td><td>
			<a href="https://github.com/jdfergason">JD Fergason</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Leaflet/Leaflet.label">Leaflet.label</a>
		</td><td>
			将文本标签添加到地图标记和矢量图层。
		</td><td>
			<a href="https://github.com/jacobtoye">Jacob Toye</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jieter/Leaflet-semicircle">Leaflet-semicircle</a>
		</td><td>
			添加了用来绘制半圆的 <code>L.Circle</code> 功能。
		</td><td>
			<a href="https://github.com/jieter">Jieter</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bbecquet/Leaflet.PolylineDecorator">Leaflet.PolylineDecorator</a>
		</td><td>
			允许您沿折线或坐标路径绘制图案（如破折号、箭头或等距标记）。
		</td><td>
			<a href="https://github.com/bbecquet">Benjamin Becquet</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/slutske22/leaflet-arrowheads">Leaflet-arrowheads</a>
		</td><td>
			允许用户在折线上快速绘制箭头，实现矢量可视化。
		</td><td>
			<a href="https://github.com/slutske22">Slutske22</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/leaflet-extras/leaflet.sprite">Leaflet.Sprite</a>
		</td><td>
			在标记中使用基于精灵（sprite）的图标。
		</td><td>
			<a href="https://github.com/calvinmetcalf">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.TextPath">Leaflet.TextPath</a>
		</td><td>
			允许您沿折线绘制文本。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iatkin/leaflet-svgicon">Leaflet-SVGIcon</a>
		</td><td>
			一个简单和可定制的SVG图标，没有外部依赖性，还包括一个方便的Marker类和两个示例子类。<a href="http://iatkin.github.io/leaflet-svgicon/">可定制的演示示例</a>。
		</td><td>
			<a href="https://github.com/iatkin">Ilya Atkin</a>
		</td>
	</tr>
    	<tr>
		<td>
			<a href="https://github.com/marslan390/BeautifyMarker">Leaflet.BeautifyMarkers</a>
		</td><td>
			轻量级插件，添加无图像的彩色标志性标记，并为最终用户提供对样式的完全控制（即无限颜色和 CSS 样式）。
		</td><td>
			<a href="https://github.com/marslan390">Muhammad Arslan Sajid</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/lvoogdt/Leaflet.awesome-markers">Leaflet.Awesome-Markers</a>
		</td><td>
            基于 Font Awesome 图标或 Twitter Bootstrap 图标的彩色的、具有标志性和防视网膜的标记
		</td><td>
			<a href="http://www.lennardvoogdt.nl">Lennard Voogdt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/coryasilva/Leaflet.ExtraMarkers">Leaflet.Extra-Markers</a>
		</td><td>
			无耻地抄袭 Awesome-Markers，提供更多形状、颜色和语义界面支持
		</td><td>
			<a href="http://www.corysilva.com">Cory Silva</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jseppi/Leaflet.MakiMarkers">Leaflet.MakiMarkers</a>
		</td><td>使用 MapBox 的 <a href="https://www.mapbox.com/maki/">Maki Icons</a> 创建标记。
		</td><td>
			<a href="https://github.com/jseppi">James Seppi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.Icon.Glyph">Leaflet.Icon.Glyph</a>
		</td><td>
			在你的标记中使用图标字体字形（来自Font Awesome, Material Design Icons, Glyphicons, Metro UI 图标、Elusive和其他图标字体) (<a href='https://ivansanchez.github.io/Leaflet.Icon.Glyph/demo.html'>demo</a>)
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.LineExtremities">Leaflet.LineExtremities</a>
		</td><td>
				使用 SVG 标记（marker）在折线的末端显示符号。
		</td><td>
			<a href="https://github.com/fredericbonifas">Frédéric Bonifas</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/hiasinho/Leaflet.vector-markers">Leaflet.VectorMarkers</a>
		</td><td>
			Leaflet 的矢量 SVG 标记，可以选择 Font Awesome/Twitter Bootstrap 图标。
		</td><td>
			<a href="https://github.com/hiasinho">Mathias Schneider</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rowanwins/Leaflet.SvgShapeMarkers">Leaflet.SvgShapeMarkers</a>
		</td><td>
添加对其他   添加对其他 SVG 标记类型的支持，例如三角形、菱形和正方形。
		</td><td>
			<a href="https://github.com/rowanwins/">Rowan Winsemius</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/teastman/Leaflet.pattern">Leaflet.pattern</a>
		</td><td>
			在路径上添加对图案填充的支持。
		</td><td>
			<a href="https://github.com/teastman">Tyler Eastman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/thomasbrueggemann/leaflet.boatmarker">Leaflet.BoatMarker</a>
		</td><td>
			一个使用HTML Canvas的船只标记，用于显示游艇和帆船的航向和可选的风力信息。<a href="http://thomasbrueggemann.github.io/leaflet.boatmarker/">演示</a>。
		</td><td>
			<a href="https://github.com/thomasbrueggemann">Thomas Brüggemann</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/heyman/leaflet-usermarker">leaflet-usermarker</a>
		</td><td>
			用于在地图上绘制代表一个用户或多个用户的标记的插件，支持绘制精度圆。可以在 <a href="http://longitude.me">Longitude.me</a> 上查看具体内容。
		</td><td>
			<a href="http://heyman.info">Jonatan Heyman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/albburtsev/Leaflet.geojsonCSS">Leaflet.geojsonCSS</a>
		</td><td>
			Leaflet 的 <a href="http://wiki.openstreetmap.org/wiki/Geojson_CSS">Geojson CSS</a> 实现。
		</td><td>
			<a href="https://github.com/albburtsev/">Alexander Burtsev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rowanwins/leaflet-simplestyle">leaflet-simplestyle</a>
		</td><td>
			扩展了 L.geoJSON，以支持 <a href="https://github.com/mapbox/simplestyle-spec">simple style</a> 规范。
		</td><td>
			<a href="https://github.com/rowanwins/">Rowan Winsemius</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://osmbuildings.org/">OSM Buildings</a>
		</td><td>
			惊人的JS库，用于在Leaflet之上实现3D OSM建筑几何的可视化。
		</td><td>
			<a href="https://github.com/kekscom/">Jan Marsch</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ubergesundheit/Leaflet.EdgeMarker">Leaflet.EdgeMarker</a>
		</td><td>
			用于指示当前视图之外的功能存在的插件。
		</td><td>
			<a href="https://github.com/ubergesundheit">Gerald Pape</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gismartwaredev/leaflet.orientedMarker">Leaflet.orientedMarker</a>
		</td><td>
			允许动态管理标记（marker）的方向。
		</td><td>
			<a href="https://github.com/gismartwaredev">Gismartwaredev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapshakers/leaflet-icon-pulse">leaflet-icon-pulse</a>
		</td><td>
			使用 CSS3 呈现脉冲图标，它可用于位置标记。
		</td><td>
			<a href="https://github.com/mapshakers">mapshakers</a>/
			<a href="https://github.com/filipzava">Filip Zavadil</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapshakers/leaflet-mapkey-icon">leaflet-mapkey-icon</a>
		</td><td>
			一套基于<a href="http://www.mapkeyicons.com">mapkeyicons</a>的制图字体图标。
		</td><td>
			<a href="https://github.com/mapshakers">mapshakers</a>/
			<a href="https://github.com/filipzava">Filip Zavadil</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/turban/Leaflet.Photo">Leaflet.Photo</a>
		</td><td>
			在Leaflet地图上显示地理标记的照片的插件。<a href="http://turban.github.io/Leaflet.Photo/examples/picasa.html">Demo</a>
		</td><td>
			<a href="https://github.com/turban">Bjørn Sandvik</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/elfalem/Leaflet.curve">Leaflet.curve</a>
		</td><td>
				用于绘制贝塞尔曲线和其他复杂形状的 Leaflet 插件。<a href="http://elfalem.github.io/Leaflet.curve/">Demo</a>
		</td><td>
			<a href="https://github.com/elfalem">elfalem</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/lifeeka/leaflet.bezier">Leaflet.bezier</a>
		</td><td>
			在两个带有动画的飞行对象之间绘制一条贝塞尔线。
		</td><td>
			<a href="https://github.com/spmsupun">Supun Praneeth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MAD-GooZe/Leaflet.Arc">Leaflet.Arc</a>
		</td><td>
				这个插件添加了 L.Polyline.Arc 函数，它包装了 arc.js 功能，用于创建大圆弧。
		</td><td>
			<a href="https://github.com/MAD-GooZe">Alexey Gusev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/timwis/leaflet-choropleth">leaflet-choropleth</a>
		</td><td>
			扩展 L.geoJson， 添加 choropleth 来进行可视化（基于值的颜色比例）。 <a href="http://timwis.com/leaflet-choropleth/examples/basic">Demo</a>.
		</td><td>
			<a href="http://timwis.com">Tim Wisniewski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/eJuke/Leaflet.Canvas-Markers">Leaflet.Canvas-Markers</a>
		</td><td>
			在画布上而不是 DOM 上显示标记（marker）。
		</td><td>
			<a href="https://github.com/eJuke">Evgeniy Voynov</a>
		</td>
	</tr>
        <tr>
                <td>
                        <a href="https://github.com/lethexa/leaflet-tracksymbol">leaflet-tracksymbol</a>
                </td><td>
                        这个标记提供了一个带有方向、速度矢量和可配置形状的轨迹符号。
                </td><td>
                        <a href="https://github.com/lethexa">Tim Leerhoff</a>
                </td>
        </tr>
        <tr>
                <td>
                        <a href="https://github.com/PowerPan/leaflet-ais-tracksymbol">leaflet-ais-tracksymbol</a>
                </td><td>
                        Leaflet-tracksymbol 的 AIS 扩展 它在地图上显示 AIS 联系人。
                </td><td>
                        <a href="https://github.com/powerpan">Johannes Rudolph</a>
                </td>
        </tr>
        <tr>
                <td>
                        <a href="https://github.com/PowerPan/leaflet-ais-tracksymbol-search">leaflet-ais-tracksymbol-search</a>
                </td><td>
                       为你的 Leaflet 地图和你的 <a href="https://github.com/PowerPan/leaflet-ais-tracksymbol">leaflet-ais-trackymbol</a> 添加一个搜索框
                </td><td>
                        <a href="https://github.com/powerpan">Johannes Rudolph</a>
                </td>
        </tr>
	<tr>
		<td>
			<a href="https://github.com/wwwouaiebe/leaflet.TravelNotes">leaflet.TravelNotes</a>
		</td>
		<td>
				传单的可编辑标记和路由引擎。路由引擎有 Mapbox、GraphHopper 和 OSRM 插件，可用于汽车、自行车或步行路线。<a href="https://wwwouaiebe.github.io/leaflet.TravelNotes/?lng=en">Demo</a>
		</td>
		<td>
			<a href="https://github.com/wwwouaiebe">Christian Guyette</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.Marker.Stack">Leaflet.Marker.Stack</a>
		</td>
		<td>
			CartoDB 的“<a href="http://blog.cartodb.com/stacking-chips-a-map-hack/">stacked chips</a>”符号的纯 Leaflet 实现。 <a href="http://ivansanchez.github.io/Leaflet.Marker.Stack/demos/color_ramps.html">Demo</a>.
		</td>
		<td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/cloudybay/leaflet-polygon-fillPattern">leaflet-polygon.fillPattern</a>
		</td>
		<td>
            扩展多边形对象以使用图像图案填充 SVG 路径元素。<a href="http://lwsu.github.io/leaflet-polygon-fillPattern/example/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/cloudybay/">CloudyBay</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bbecquet/Leaflet.PolylineOffset">Leaflet Polyline Offset</a>
		</td>
		<td>
			为<code>L.Polyline</code>增加了以相对像素偏移的能力，而不修改其实际的<code>LatLng</code>s。该偏移值可以是负的或正的，用于左侧或右侧的偏移，并且在不同的缩放级别中保持不变（<a href="http://bbecquet.github.io/Leaflet.PolylineOffset/examples/example.html">基本演示</a>）。
		</td>
		<td>
			<a href="https://github.com/bbecquet">Benjamin Becquet</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/w8r/leaflet-labeled-circle">leaflet-labeled-circle</a>
		</td>
		<td>
			特殊类型的 SVG 标记，内部带有标签并可围绕锚点拖动 (<a href="https://w8r.github.io/leaflet-labeled-circle/demo/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/w8r/">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dagjomar/Leaflet.ParallaxMarker">Leaflet.ParallaxMarker</a>
		</td>
		<td>
            添加在平移时相对于地图具有视差效果的标记(<a href="https://dagjomar.github.io/Leaflet.ParallaxMarker/">demos / examples</a>).
		</td>
		<td>
			<a href="https://github.com/dagjomar/">Dag Jomar Mersland</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/adoroszlai/leaflet-distance-markers">leaflet-distance-markers</a>
		</td>
		<td>
			允许沿路线（L.Polyline）以等效距离（例如每英里一个）显示标记 (<a href="http://adoroszlai.github.io/leaflet-distance-markers/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/adoroszlai">Doroszlai, Attila</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mikhailshilkov/leaflet-corridor">leaflet-corridor</a>
		</td>
		<td>
            以米为单位呈现宽度固定的折线，而不是以像素为单位；根据缩放级别调整宽度 (<a href="http://mikhail.io/demos/leaflet-corridor/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/mikhailshilkov">Mikhail Shilkov</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yakitoritabetai/Leaflet.LabelTextCollision">Leaflet.LabelTextCollision</a>
		</td>
		<td>
			在路径（折线、多边形、圆）上显示标签以避免标签冲突 (<a href="https://yakitoritabetai.github.io/Leaflet.LabelTextCollision/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/yakitoritabetai">Kenta Hakoishi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/triedeti/Leaflet.streetlabels">Leaflet.streetlabels</a>
		</td>
		<td>
			一个 Leaflet 插件，用于显示跟随折线路径的标签，是yakitoritabetai Leaflet.LabelTextCollision的扩展 (<a href="https://triedeti.github.io/Leaflet.streetlabels/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/triedeti">Triede TI</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ggolikov/Leaflet.Viewpoint">Leaflet.Viewpoint</a>
		</td>
		<td>
            显示具有多个方向的 circleMarker。用于显示从一个点拍摄的照片 (<a href="https://ggolikov.github.io/Leaflet.Viewpoint/example/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/ggolikov">Grigory Golikov</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/react-map/leaflet.magicMarker">Leaflet.magicMarker</a>
		</td>
		<td>
            在加载时为标记添加神奇的动画效果 (<a href="https://react-map.github.io/leaflet.magicMarker/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/react-map">Sylvenas</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/brandonxiang/leaflet.marker.highlight">Leaflet.Marker.Highlight</a>
		</td>
		<td>
			为 L.Marker 增加亮点表现 (<a href="https://brandonxiang.github.io/leaflet.marker.highlight/examples/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/brandonxiang">Brandon Xiang</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/nypl-spacetime/Leaflet.GeotagPhoto">Leaflet.GeotagPhoto</a>
		</td>
		<td>
			用于照片地理标记的插件，具有两种模式：相机和十字准线 (<a href="http://spacetime.nypl.org/Leaflet.GeotagPhoto/examples/camera.html">Demo</a>).
		</td>
		<td>
			<a href="https://github.com/bertspaan">Bert Spaan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.GLMarkers">Leaflet.GLMarkers</a>
		</td><td>
			使用自定义 WebGL 着色器显示数千个标记，可选动画 (<a href='http://https://ivansanchez.gitlab.io/Leaflet.GLMarkers/demo/repl.html'>demo</a>)
		</td><td>
			<a href="https://gitlab.com/IvanSanchez">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ggolikov/Leaflet.River">Leaflet.River</a>
		</td>
		<td>
            在地图上绘制不同宽度的线（如河流），当您想在地图上显示河流如何“流动”时很有用 (<a href="https://ggolikov.github.io/Leaflet.River/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/ggolikov">Grigory Golikov</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sybri/Leaflet.SpeechBubble/">Leaflet.SpeechBubble</a>
		</td>
		<td>
			弹出一个带有跟随点（point）、图层（layer）、标记（marker）的箭头的对话气泡 (<a href="https://sybri.github.io/demo/Leaflet.SpeechBubble/demo.html">demo</a>)
		</td>
		<td>
			<a href="https://github.com/sybri">Sylvain BRISSY</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://wbkd.github.io/leaflet-swoopy/">Leaflet Swoopy</a>
		</td>
		<td>
            用于创建可定制的 swoopy 箭头注释的插件。
		</td>
		<td>
			<a href="https://webkid.io">webkid</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Oliv/leaflet-polycolor">leaflet-polycolor</a>
		</td>
		<td>
			为每个折线着色 (<a href='https://oliv.github.io/leaflet-polycolor/'>demo</a>)
		</td>
		<td>
			<a href="https://github.com/Oliv">Olivier Gasc</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/JackZouShao/leaflet-marker-direction">leaflet-marker-direction</a>
		</td>
		<td>
			显示标记的路径和方向 (<a href='https://jackzoushao.github.io/leaflet-marker-direction/examples/marker-direction.html'>demo</a>)
		</td>
		<td>
			<a href="https://github.com/JackZouShao">Jack Zou</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bbecquet/Leaflet.RotatedMarker">Leaflet Rotated Marker</a>
		</td>
		<td>
            启用 Leaflet 中标记图标的旋转 (<a href='http://bbecquet.github.io/Leaflet.RotatedMarker/example.html'>Demo</a>)
		</td>
		<td>
			<a href="https://github.com/bbecquet">Benjamin Becquet</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://wbkd.github.io/leaflet-truesize/">Leaflet Truesize</a>
		</td>
		<td>
			用于创建投影感知可拖动多边形和折线的插件
		</td>
		<td>
			<a href="https://webkid.io">webkid</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.RepeatedMarkers">Leaflet.RepeatedMarkers</a>
		</td>
		<td>
			绕过地球时显示标记，每360度经度显示一次 (<a href="https://ivansanchez.gitlab.io/Leaflet.RepeatedMarkers/demo.html">demo</a>)
		</td>
		<td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/henrythasler/Leaflet.Geodesic">Leaflet.Geodesic</a>
		</td><td>
            绘制测地线和圆。测地线是地球表面上两个给定点之间的最短路径。它使用 Vincenty 的公式进行最高精度和距离计算。用 Typescript 编写，可通过 CDN 获得 <a href="https://blog.cyclemap.link/Leaflet.Geodesic/complex-interactive.html">Demo</a>
		</td><td>
			<a href="https://github.com/henrythasler">Henry Thasler</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/nuclearsecrecy/Leaflet.greatCircle">Leaflet.greatCircle</a>
		</td>
		<td>
			一个Leaflet.js Polygon对象的封装类，用于绘制环绕地球的真正的 "大圆"（显示真正的测地线、球面路径） (<a href="https://nuclearsecrecy.github.io/Leaflet.greatCircle/example/">demo</a>
		</td>
		<td>
			<a href="https://github.com/nuclearsecrecy/">Alex Wellerstein</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iDerekLi/Leaflet.CustomLayer">Leaflet.CustomLayer</a>
		</td>
		<td>
			一个 Leaflet 插件 L.CustomLayer - 完全自定义的 Layer
		</td>
		<td>
			<a href="https://github.com/iDerekLi/">Derek Li</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/coyotesqrl/Leaflet.ArrowCircle">Leaflet.ArrowCircle</a>
		</td>
		<td>
            用于显示带有方向箭头的圆圈的标记扩展
		</td>
		<td>
			<a href="https://github.com/coyotesqrl/">R.A. Porter</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/phloose/leaflet-layervisibility">leaflet-layervisibility</a>
		</td>
		<td>
			Extends L.Layer and L.LayerGroup with methods to hide/show layers without removing/re-adding them.
		</td>
		<td>
			<a href="https://github.com/phloose/">Philipp Loose</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/heyman/leaflet-centermarker">Leaflet.CenterMarker</a>
		</td><td>
			Marker that is kept fixed to the center of the map when the map is panned by dragging.
			Can be seen in action on <a href="https://whatismyaddress.net/">What is my adress?</a>
		</td><td>
			<a href="http://heyman.info">Jonatan Heyman</a>
		</td>
	</tr>
    <tr>
        <td>
            <a href="https://github.com/Falke-Design/L.Donut">L.Donut</a>
        </td>
        <td>
           Extension of L.Circle which allows to define a outer and inner radius. <a href="https://falke-design.github.io/L.Donut/">Demo</a>
        </td>
        <td>
            <a href="https://github.com/Falke-Design/">Falke-Design</a>
        </td>
    </tr>
	<tr>
		<td>
			<a href="https://github.com/FacilMap/Leaflet.HighlightableLayers">Leaflet.HighlightableLayers</a>
		</td>
		<td>
			Highlight Leaflet lines and polygons by adding a border and raising them above others. Add a transparent border to increase the tolerance for mouse/touch interactions. <a href="https://unpkg.com/leaflet-highlightable-layers/example.html">Demo</a>
		</td>
		<td>
			<a href="https://github.com/cdauth/">Candid Dauth</a>
		</td>
	</tr>
</table>



### Overlay animations

这些插件对标记物或一些几何图形进行动画处理。另请参阅[带时间或海拔的几何图形](#geometryinteraction-time)。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/openplans/Leaflet.AnimatedMarker">Leaflet.AnimatedMarker</a>
		</td><td>
			沿着多段线为一个标记制作动画。
		</td><td>
			<a href="https://github.com/atogle">Aaron Ogle</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/maximeh/leaflet.bouncemarker">Leaflet.BounceMarker</a>
		</td><td>
            将标记添加到地图时使标记弹跳。
		</td><td>
			<a href="https://github.com/maximeh">Maxime Hadjinlian</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/hosuaby/Leaflet.SmoothMarkerBouncing">Leaflet.SmoothMarkerBouncing</a>
		</td><td>
			为 Leaflet 的标记添加平滑的弹跳动画。
		</td><td>
			<a href="https://github.com/hosuaby">Alexei KLENIN</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ewoken/Leaflet.MovingMarker">Leaflet.MovingMarker</a>
		</td><td>
			允许以自定义的持续时间沿多段线移动标记。
		</td><td>
			<a href="https://github.com/ewoken">Ewoken</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/naturalatlas/leaflet-transitionedicon">Leaflet.TransitionedIcon</a>
		</td><td>
			使用 CSS3 动画过渡 进入/移除 的标记。它支持抖动，将标记交错进入视图以防止视觉过载。查看 <a href="http://naturalatlas.github.io/leaflet-transitionedicon/">demo</a>
		</td><td>
			<a href="https://github.com/brianreavis">Brian Reavis</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.Polyline.SnakeAnim">Leaflet.Polyline.SnakeAnim</a>
		</td><td>
			将（多角）线动画化，就像它们被慢慢地从头画到尾一样。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.Path.DashFlow">Leaflet.Path.DashFlow</a>
		</td><td>
			对直线和圆圈的 dashArray 进行动画处理，创造一个基本的流动效果。(<a href="https://ivansanchez.gitlab.io/Leaflet.Path.DashFlow/demo.html">Demo</a>
		</td><td>
			<a href="https://gitlab.com/IvanSanchez">Iván Sánchez Ortega</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rubenspgcavalcante/leaflet-ant-path">Leaflet.AntPath</a>
		</td><td>
			Leaflet.AntPath将一个通量动画（如蚂蚁行走）放入Polyline。
			(<a href='http://rubenspgcavalcante.github.io/leaflet-ant-path/'>demo</a>)
		</td><td>
			<a href="https://github.com/rubenspgcavalcante">Rubens Pinheiro</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/IvanSanchez/Leaflet.Marker.SlideTo">Leaflet.Marker.SlideTo</a>
		</td><td>
			平稳地移动（滑动）标记到一个新的位置。 (<a href='http://ivansanchez.gitlab.io/Leaflet.Marker.SlideTo/demo.html'>demo</a>)
		</td><td>
			<a href="https://gitlab.com/u/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Igor-Vladyka/leaflet.motion">leaflet.motion</a>
		</td><td>
			将简单的运动添加到你的多段线上，并在线头处设置标记。 (<a href='https://igor-vladyka.github.io/leaflet.motion/'>demo</a>)
		</td><td>
			<a href="https://github.com/Igor-Vladyka/">Igor Vladyka</a>,
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ggolikov/Leaflet.Rain">Leaflet.Rain</a>
		</td>
		<td>
			用于 Leaflet 的可定制的 WebGL 下雨动画，对天气图很有用。 (<a href="https://ggolikov.github.io/Leaflet.Rain/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/ggolikov">Grigory Golikov</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ggolikov/Leaflet.Snow">Leaflet.Snow</a>
		</td>
		<td>
			用于 Leaflet 的可定制的 WebGL 雪景动画，适用于天气图。 (<a href="https://ggolikov.github.io/Leaflet.Snow/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/ggolikov">Grigory Golikov</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/onaci/leaflet-point-animator">leaflet-point-animator</a>
		</td>
		<td>
			为大量的 GeoJSON 点制作动画。 (<a href="https://onaci.github.io/leaflet-point-animator">demo</a>)
		</td>
		<td>
			<a href="https://github.com/danwild">danwild</a>, <a href="https://github.com/onaci">onaci</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/onaci/leaflet-temporal-geojson">leaflet-temporal-geojson</a>
		</td>
		<td>
			灵活的 GeoJSON feature 的动画。 (<a href="https://onaci.github.io/leaflet-temporal-geojson">demo</a>)
		</td>
		<td>
			<a href="https://github.com/danwild">danwild</a>, <a href="https://github.com/onaci">onaci</a>
		</td>
	</tr>
	</table>



### Clustering/Decluttering

当您显示大量数据时，这些插件将使您的地图看起来更干净。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/Leaflet/Leaflet.markercluster">Leaflet.markercluster</a>
		</td><td>
			美丽、精致、高性能的标记群集解决方案，具有流畅的动画和许多强大的功能。<em>强烈推荐！</em>。
		</td><td>
			<a href="https://github.com/danzel">Dave Leaver</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MazeMap/Leaflet.LayerGroup.Collision">Leaflet.LayerGroup.Collision</a>
		</td><td>
			为标记群提供碰撞检测。与聚类不同，它考虑到了标记的形状&amp; 大小。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jawj/OverlappingMarkerSpiderfier-Leaflet">Overlapping Marker Spiderfier</a>
		</td><td>
			以谷歌地球启发的方式处理重叠的标记，在点击时优雅地将它们弹开。
		</td><td>
			<a href="http://mackerron.com">George MacKerron</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/SINTEF-9012/PruneCluster">PruneCluster</a>
		</td><td>
            快速实时的标记聚类库。
		</td><td>
			<a href="https://github.com/yellowiscool">Antoine Pultier</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/oliverroick/Leaflet.Deflate">Leaflet.Deflate</a>
		</td><td>
			当线条和多边形在较低的缩放级别中屏幕尺寸变得太小时，将其放缩为一个标记。
		</td><td>
			<a href="https://github.com/oliverroick">Oliver Roick</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/andy-kay/Leaflet.GridCluster">Leaflet.GridCluster</a>
		</td><td>
			实时创建基于网格的集群。
		</td><td>
			<a href="https://github.com/andy-kay">Andreas Kiefer</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/spatialdev/q-cluster">q-cluster</a>
		</td><td>
			带有D3分类的快速点聚类库。
		</td><td>
			<a href="https://github.com/hallahan">Nicholas Hallahan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Eclipse1979/leaflet-conditionalLayer">Leaflet.ConditionalLayer</a>
		</td><td>
			在视口中不显示超过一定数量可见标记的要素组。(<a href="http://eclipse1979.github.io/Leaflet.ConditionalLayer/example/leaflet-conditionalLayer2.html">Demo</a>)
		</td><td>
			<a href="https://github.com/Eclipse1979">EPP</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ghybs/Leaflet.FeatureGroup.SubGroup">Leaflet.FeatureGroup.SubGroup</a>
		</td><td>
			一个简单的插件，用于创建特征组，将其子层添加到父组中。典型的用法是通过 L.Control.Layers 来切换它们，动态地添加/删除 Leaflet.markercluster 中的标记组。 <a href="http://ghybs.github.io/Leaflet.FeatureGroup.SubGroup/examples/subGroup-markercluster-controlLayers-realworld.388.html">Demo</a>
		</td><td>
			<a href="https://github.com/ghybs">ghybs</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ZijingPeng/leaflet-tooltip-layout">leaflet-tooltip-layout</a>
		</td><td>
			一个避免工具提示重叠的插件，使其更容易找出每个工具提示和标记之间的关系。 <a href="https://zijingpeng.github.io/overlapping-avoided-tooltip/">Demo</a>
		</td><td>
			<a href="https://github.com/ZijingPeng">Zijing Peng</a>
		</td>
	</tr>
</table>

### Heatmaps

这些插件使用矢量数据创建可视化的热力图或类似热力图的图像。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/domoritz/leaflet-maskcanvas">MaskCanvas</a>
		</td><td>
			画布层，可用于可视化覆盖。
		</td><td>
			<a href="https://github.com/domoritz">Dominik Moritz</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sunng87/heatcanvas">HeatCanvas</a>
		</td><td>
			基于 HTML5 canvas 的简单的热力图 api。
		</td><td>
			<a href="https://github.com/sunng87">Sun Ning</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://www.patrick-wied.at/static/heatmapjs/example-heatmap-leaflet.html">heatmap.js</a>
		</td><td>
			基于 HTML5 canvas 的热力图的 JavaScript 库。
			其 Leaflet 层的实现支持大型数据集，因为它是基于瓦片的，并使用四叉树索引来存储数据。
		</td><td>
			<a href="https://github.com/pa7">Patrick Wied</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dpiccone/leaflet-div-heatmap">Leaflet divHeatmap</a>
		</td><td>
			基于 CSS3 和 divIcons 的轻量级和多功能热力图图层
		</td><td>
			<a href="https://github.com/dpiccone">Daniele Piccone</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://ursudio.com/webgl-heatmap-leaflet/">WebGL Heatmap</a>
		</td><td>
            使用 WebGL 的高性能 Javascript 热力图插件。
		</td><td>
			<a href="http://ursudio.com/webgl-heatmap-leaflet/">Benjamin J DeLong</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Leaflet/Leaflet.heat">Leaflet.heat</a>
		</td><td>
			一个微小、简单、快速的 Leaflet 热力图插件。在引擎盖下使用 <a href='https://github.com/mourner/simpleheat'>simpleheat</a>，另外还将点聚成一个网格以提高性能。(<a href='https://leaflet.github.io/Leaflet.heat/demo'>Demo</a>)
		</td><td>
			<a href="https://github.com/mourner">Vladimir Agafonkin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mejackreed/leaflet-solr-heatmap">Leaflet-Solr-Heatmap</a>
		</td><td>
			一个 Leaflet 插件，用于渲染来自 <a href='https://lucene.apache.org/solr/guide/6_6/spatial-search.html#SpatialSearch-HeatmapFaceting'>Solr 的 Heatmap Faceting</a> 的热力图和群集，对于数以百万计的点或多边形具有很高的性能。
		</td><td>
			<a href="https://github.com/mejackreed">Jack Reed</a> /
			<a href="https://github.com/spacemansteve">Steve McDonald</a>
		</td>
	</tr>
</table>


### DataViz

用于数据可视化的强大多用途库。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/giscience/geogrid.js">geogrid.js</a>
		</td><td>
			显示由 ISEA3H 离散全球网格系统聚合的数据。例如，通过使用 <a href="https://github.com/giscience/measures-rest">Measures REST</a>（一个框架，提供由网格聚合的数据）或 <a href="https://github.com/giscience/geogrid">geogrid</a>（一个库，用于处理网格，以防你想手动聚合数据）来交付。
		</td><td>
			<a href="http://www.mocnik-science.net">F.-B. Mocnik,</a><br><a href="http://www.geog.uni-heidelberg.de/gis/index_en.html">GIScience Research Group,<br>Heidelberg University</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://dynmeth.github.com/RaphaelLayer/">RaphaelLayer</a>
		</td><td>
			允许您将 <a href="http://raphaeljs.com/">Raphael</a> 用作 Leaflet 地图上的图层，以实现高级动画和可视化。
		</td><td>
			<a href="https://github.com/dynmeth">Dynamic Methods</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://humangeo.github.com/leaflet-dvf/">Leaflet Data Visualization Framework</a>
		</td><td>
			新的标记、图层和实用程序类，可轻松实现专题制图和数据可视化。
		</td><td>
			<a href="https://github.com/sfairgrieve">Scott Fairgrieve</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/teralytics/Leaflet.D3SvgOverlay">Leaflet.D3SvgOverlay</a>
		</td><td>
			用于与<a href="http://d3js.org">D3</a>库一起使用的SVG叠加类。支持缩放动画和缩放，不需要重新绘制图层。
		</td><td>
			<a href="https://github.com/xEviL">Kirill Zhuravlev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapbox/mapbox-gl-leaflet">mapbox-gl-leaflet</a>
		</td><td>
            从 Mapbox GL JS 绑定到 Leaflet API
		</td><td>
			<a href="https://github.com/tmcw">Tom MacWright</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/wandergis/leaflet-echarts">leaflet-echarts</a>
		</td><td>
            Leaflet 插件加载 <a href="https://github.com/ecomfe/echarts">echarts</a> 地图，让大数据可视化更简单。
		</td><td>
			<a href="https://github.com/wandergis">wandergis</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/atlefren/storymap">jquery-storymap</a>
		</td><td>
			一个 jQuery 插件，用于在用户滚动段落时显示多个地图位置。
		</td><td>
			<a href="https://github.com/atlefren">Atle Frenvik Sveen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rstudio/leaflet">Leaflet for R</a>
		</td><td>
			允许在 <a href="https://en.wikipedia.org/wiki/R_%28programming_language%29">R</a> 程序中使用 Leaflet，这是一种流行于统计分析和数据挖掘的编程语言。
		</td><td>
			<a href="https://github.com/rstudio/">RStudio team</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/react-map/leaflet.migrationLayer">leaflet.migrationLayer</a>
		</td><td>
			leaflet.migrationLayer 用来显示人口、航班、车辆、交通等迁移数据并在地图上进行数据可视化。<a href="https://react-map.github.io/leaflet.migrationLayer">demo</a>
		</td><td>
			<a href="https://github.com/react-map">Sylvenas</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://ibesora.github.io/Leaflet.Quadtree/">Leaflet.Quadtree</a>
		</td><td>
			Leaflet.Quadtree 是用于检索给定范围内的可见数据。
		</td><td>
			<a href="https://github.com/ibesora">ibesora</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jwasilgeo/Leaflet.Canvas-Flowmap-Layer">Leaflet.Canvas-Flowmap-Layer</a>
		</td><td>
			一个 LeafletJS 的自定义地图图层，用于在 HTML 画布上用贝塞尔曲线绘制物体、想法、人等的流动。
		</td><td>
			<a href="https://github.com/jwasilgeo">Jacob Wasilkowski</a>,
			<a href="https://github.com/sarahbellum">Sarah Bell</a>
    </td>
  </tr>
  <tr>
    <td>
			<a href="https://github.com/manubb/Leaflet.PixiOverlay">Leaflet.PixiOverlay</a>
		</td><td>
            可以使用 <a href="http://www.pixijs.com/">Pixi.js</a> 绘制和执行动画的 Leaflet 覆盖类。(<a href="https://manubb.github.io/Leaflet.PixiOverlay/demo.html">demo</a>)
		</td><td>
			<a href="https://github.com/manubb">Manuel Baclet</a>
		</td>
	</tr>
	 <tr>
        <td>
    		<a href="https://github.com/danwild/leaflet-velocity">leaflet-velocity</a>
    	</td>
    	<td>
            使用 Leaflet 可视化 velocity 图层。
            <a href="https://danwild.github.io/leaflet-velocity">Demo</a>
        </td>
        <td>
            <a href="https://github.com/danwild">Dan Wild</a>
        </td>
    </tr>
	 <tr>
        <td>
    		<a href="https://github.com/locknono/leaflet-partition">leaflet-partition</a>
    	</td>
    	<td>
            以不同的方式将区域划分为多个部分，例如 voronoi（三角剖分）和六边形平铺。
            <a href="https://locknono.github.io/leaflet-partition/">Basic demo</a>
        </td>
        <td>
            <a href="https://github.com/locknono">locknono</a>
        </td>
    </tr>
	<tr>
		<td>
			<a href="https://github.com/robertleeplummerjr/Leaflet.glify">Leaflet.glify</a>
		</td>
		<td>
			Fast rendering for large (+100MB) GeoJSON datasets with WebGL
			<a href="https://robertleeplummerjr.github.io/Leaflet.glify">Demo</a>
		</td>
		<td>
			<a href="https://github.com/robertleeplummerjr">robertleeplummerjr</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/onaci/Leaflet.glify.layer">Leaflet.glify.layer</a>
		</td>
		<td>
			Add-on for the Leaflet.glify plugin to provide more leaflet-idiomatic bindings. Provides fast webgl rendering for GeoJSON FeatureCollections (currently limited to polygons, lines and points).
			<a href="https://onaci.github.io/Leaflet.glify.layer/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/onaci">onaci</a>
		</td>
	</tr>
</table>



## Interaction with geometries/features

以下插件使用户能够与叠加数据互动：编辑几何图形，选择区域或特征，与时间维度互动，搜索特征并显示有关信息。

* [编辑几何图形](#edit-geometries)
* [时间 & 海拔](#time--elevation)
* [搜索 & 弹出框](#search--popups)
* [区域/覆盖选择](#areaoverlay-selection)

### Edit geometries

允许用户创建、绘制、编辑和/或删除点、线和多边形。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/geoman-io/leaflet-geoman">Leaflet-Geoman</a>
		</td><td>
			⭐ Leaflet 1.0 及更高版本的几何管理。绘制、编辑、剪切、拖动和捕捉图层，如标记、圆形、矩形、折线、多边形、图层组、geoJSON、MultiPolygons、MultiLineStrings。支持多边形孔洞、捕捉、画布模式等 (<a href="https://geoman.io/leaflet-geoman">Demo</a>)
		</td><td>
			<a href="https://github.com/codeofsumit">Sumit Kumar</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Wildhoney/Leaflet.FreeDraw">Leaflet.FreeDraw</a>
		</td><td>
			受 Zoopla 启发，使用 Leaflet.js 和 D3 创建自由的手绘多边形。
		</td><td>
			<a href="https://github.com/Wildhoney">Wildhoney</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/scripter-co/leaflet-plotter">Leaflet.plotter</a>
		</td><td>
			leaflet-plotter 允许你使用一个由 leaflet 驱动的地图来创建路线。你可以点击中间的点来创建一个新的、可拖动的点。
		</td><td>
			<a href="https://github.com/scripter-co">Nathan Mahdavi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tkrajina/leaflet-editable-polyline">Leaflet.Editable.Polyline</a>
		</td><td>可编辑的折线：移动现有的点，添加新的点和分割折线。
		</td><td>
			<a href="https://github.com/tkrajina">Tomo Krajina</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Leaflet/Leaflet.draw">Leaflet.draw</a>
		</td><td>
			通过一个带有图标和提示的非常漂亮的用户友好界面，实现了多段线、多边形、矩形、圆和标记等绘图功能。<em>强烈推荐！</em>。
		</td><td>
			<a href="https://github.com/jacobtoye">Jacob Toye</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/kartena/Leaflet.EditableHandlers">Leaflet.EditableHandlers</a>
		</td><td>
			一组插件，包括圆形编辑、测量工具和多边形边的标签。
		</td><td>
			<a href="http://www.kartena.se/">Kartena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dwilhelm89/Leaflet.StyleEditor">Leaflet.StyleEditor</a>
		</td><td>
			可以用图形用户界面编辑要素（feature）（线、多边形等）和标记的样式。
		</td><td>
			<a href="https://github.com/dwilhelm89">Dennis Wilhelm</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jdomingu/Leaflet.SimpleMarkers">Leaflet.SimpleMarkers</a>
		</td><td>
			用于添加和删除标记的轻量级 Leaflet 插件。
		</td><td>
			<a href="https://github.com/jdomingu">Jared Dominguez</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.Editable">Leaflet.Editable</a>
		</td><td>
			轻量级的完全可定制和可控制的绘图/编辑插件。
		</td><td>
			<a href="http://yohanboniface.me/">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/w8r/Leaflet.Path.Drag">Leaflet.Path.Drag</a>
		</td>
		<td>
			多边形和折线的拖动处理和交互程序 (<a href="https://w8r.github.io/Leaflet.Path.Drag">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/w8r/">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/w8r/Leaflet.Path.Transform">Leaflet.Path.Transform</a>
		</td>
		<td>
			多边形和折线的缩放和旋转处理和交互程序 (<a href="https://w8r.github.io/Leaflet.Path.Transform">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/w8r/">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.Snap">Leaflet.Snap</a>
		</td><td>
            启用可拖动标记与折线和其他图层的对齐。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/willfarrell/Leaflet.Clipper">Leaflet.Clipper</a>
		</td><td>
			允许对两个多边形进行并联、差分、Xor和交叉操作。 (<a href="https://willfarrell.github.io/Leaflet.Clipper">Demo</a>)
		</td><td>
			<a href="https://github.com/willfarrell">will Farrell</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/SINTEF-9012/Leaflet.MapPaint">Leaflet.MapPaint</a>
		</td>
		<td>
			专为触摸设备设计的位图绘画插件。
		</td><td>
			<a href="https://github.com/yellowiscool">Antoine Pultier</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.Storage">Leaflet.Storage</a>
		</td><td>
			创建/更新/删除地图、标记、多边形、折线......并通过API将其暴露以供后端存储。
		</td><td>
			<a href="http://yohanboniface.me/">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Wildhoney/L.Pather">Leaflet.Pather</a>
		</td><td>
            L.Pather 是一个手绘折线创建器，它简化了折线的可变性。需要 D3 支持。
		</td><td>
			<a href="https://github.com/Wildhoney">Wildhoney</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/manleyjster/Leaflet.Illustrate">Leaflet.Illustrate</a>
		</td><td>
			Leaflet.draw 的扩展，使用户能够<a href="http://manleyjster.github.io/Leaflet.Illustrate/examples/0.0.2/simple/">直接在地图上输入注释</a>。
		</td><td>
			<a href="https://github.com/manleyjster">Justin Manley</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/kklimczak/Leaflet.Pin">Leaflet.Pin</a>
		</td><td>
			在使用Leaflet.Draw绘制或编辑功能时，能够将标记添加到其他图层上。
		</td><td>
			<a href="https://github.com/kklimczak">Konrad Klimczak</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tcoupin/leaflet-paintpolygon">L.Control.PaintPolygon</a>
		</td><td>
            用像 Paint[brush] 这样的圆形画笔绘制你的多边形。需要依赖于 turf.js。
		</td><td>
			<a href="https://github.com/tcoupin">Thibault Coupin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sagarpreet-chadha/Leaflet-Craft">Leaflet-Craft</a>
		</td><td>
			扩展 Leaflet.FreeDraw 并提供扩展功能，如撤消重做、删除标记、多边形的动态区域计算、各种钩子/事件和内置控制栏等。
		</td><td>
			<a href="https://github.com/sagarpreet-chadha">Sagarpreet Chadha</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Lemaf/leaflet-polyline-segment-edit">Leaflet.SegmentEdit</a>
		</td><td>
			Leaflet.draw 的扩展，允许一次编辑一个大的多段线。
		</td><td>
			<a href="https://github.com/Lemaf">Lemaf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/FacilMap/Leaflet.DraggableLines">Leaflet.DraggableLines</a>
		</td>
		<td>
			Add/move/remove points on routes, lines and polygons by drag&drop. <a href="https://unpkg.com/leaflet-draggable-lines/example.html">Demo</a>
		</td>
		<td>
			<a href="https://github.com/cdauth/">Candid Dauth</a>
		</td>
	</tr>
</table>


### Time & elevation

大多数数据是二维的（经度和纬度），但有些数据有更多维度（高度和/或时间）。以下插件可以帮助用户浏览这些额外的维度。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/slutske22/leaflet-topography">Leaflet Topography</a>
		</td>
		<td>
			一套用于以闪电般的速度计算和可视化地形数据（海拔、坡度、长宽）的工具。 基于Mapbox RGB编码的DEM瓦片。
		</td>
		<td>
			<a href="https://github.com/slutske22">Seth Lutske</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/svitkin/leaflet-timeline-slider/">Leaflet.timelineSlider</a>
		</td>
		<td>
			Leaflet 插件，可创建具有用户设计功能的可自定义时间线滑块。时间线的原始实现位于 https://codepen.io/trevanhetzel/pen/rOVrGK。
		</td>
		<td>
			<a href="https://github.com/svitkin">Sol Vitkin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/socib/Leaflet.TimeDimension">Leaflet.TimeDimension</a>
		</td>
		<td>
			在 leaflet 地图上添加时间维度功能 <a href="http://apps.socib.es/Leaflet.TimeDimension/examples/index.html">Demos</a>
		</td>
		<td>
			<a href="http://www.socib.eu">ICTS SOCIB</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dwilhelm89/LeafletSlider">Leaflet Time-Slider</a>
		</td><td>
			Leaflet Time-Slider 使您能够使用 JQuery UI 滑块在地图上动态添加和删除标记
		</td><td>
			<a href="https://github.com/dwilhelm89">Dennis Wilhelm</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/hallahan/LeafletPlayback">LeafletPlayback</a>
		</td><td>
			播放与时钟同步的带时间戳的 GPS 轨迹。
		</td><td>
			<a href="http://theoutpost.io">Nicholas Hallahan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/skeate/Leaflet.timeline">Leaflet.timeline</a>
		</td><td>
			使用时间线滑块和播放按钮在地图上显示任意 GeoJSON。
		</td><td>
			<a href="https://github.com/skeate">Jonathan Skeate</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MrMufflon/Leaflet.Elevation">Leaflet.Elevation</a>
		</td><td>
			一个 Leaflet 插件，使用 <a href="http://d3js.org/">d3</a> 查看 GeoJSON 线的交互式高度剖面。
		</td><td>
			<a href="https://github.com/MrMufflon">Felix Bache</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/GIScience/Leaflet.Heightgraph">Leaflet.Heightgraph</a>
		</td><td>
			受 Leaflet.Elevation 的启发，这个Leaflet插件允许你查看以 GeoJSON 形式存储的交互式高度剖面，其特点是可以将任意分段（如表面类型或陡峭度类别）以自定义颜色存储在 GeoJSON 本身的属性中。
		</td><td>
			<a href="https://github.com/boldtrn">Robin Boldt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iosphere/Leaflet.hotline">Leaflet.hotline</a>
		</td><td>
			用于沿折线绘制渐变的 Leaflet 插件。
		</td><td>
			<a href="https://github.com/iosphere">iosphere</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/linghuam/Leaflet.TrackPlayBack">leaflet.TrackPlayBack</a>
		</td>
		<td>
			一个 Leaflet 曲目播放插件，可以显示和动态播放曲目。 <a href="https://linghuam.github.io/Leaflet.TrackPlayBack/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/linghuam">linghuam</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/zimmicz/Leaflet-Timeline-Control">Leaflet Timeline Control</a>
		</td>
		<td>
			无限制的时间线控件，可帮助您显示时间序列数据。 <a href="https://codesandbox.io/s/leaflet-timeline-control-ibyby">Demo</a>
		</td>
		<td>
			<a href="https://github.com/zimmicz">Michal Zimmermann</a>
		</td>
	</tr>
</table>




### Search & popups

搜索叠加层并增强如何显示有关叠加层的信息的插件。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/naomap/leaflet-fusesearch">leaflet-fusesearch</a>
		</td><td>
			使用轻量级模糊搜索 Fuse.js 提供的面板在 GeoJSON 层中搜索要素的控件
		</td><td>
			<a href="http://www.naomap.fr">Antoine Riche</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-search">Leaflet Search</a>
		</td><td>
			通过 LayerGroup/GeoJSON 中的自定义属性控制搜索标记/特征位置。支持 AJAX/JSONP、自动完成和 3rd 方服务
		</td><td>
			<a href="http://labs.easyblog.it">Stefano Cudini</a>
		</td>
	</tr>
	<tr>
        	<td>
            		<a href="https://github.com/8to5Developer/leaflet-custom-searchbox">leaflet-custom-searchbox</a>
        	</td>
		<td>
                    一个谷歌地图风格的搜索框，其中包括一个侧面板滑块控件。
        	</td>
		<td>
		        <a href="https://github.com/8to5Developer/">A.D</a>
			</td>
          </tr>
	<tr>
		<td>
			<a href="https://github.com/luka1199/Leaflet.AnimatedSearchBox">Leaflet.AnimatedSearchBox</a>
		</td>
		<td>
			A simple Leaflet plugin that provides a collapsible search box.
		</td>
		<td>
			<a href="https://github.com/luka1199/">Luka Steinbach</a>
		</td>
    	<tr>
		<td>
			<a href="http://erictheise.github.com/rrose">Leaflet.Rrose</a>
		</td><td>
			一个针对边缘案例的Leaflet插件。当您希望在鼠标悬停时弹出窗口而不是单击时使用，并且您需要在靠近地图边缘时重新定位弹出提示。
		</td><td>
			<a href="http://www.linkedin.com/in/erictheise">Eric Theise</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/danzel/Leaflet.utfgrid">Leaflet.utfgrid</a>
		</td><td>
			为 leaflet 提供了一个占用的空间非常小的 utfgrid 交互处理程序。
		</td><td>
			<a href="https://github.com/danzel">Dave Leaver</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.RevealOSM">Leaflet.RevealOSM</a>
		</td><td>
			非常简单但可扩展的 Leaflet 插件，用于在地图点击时显示 OSM POI 数据。
		</td><td>
			<a href="http://yohanboniface.me">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/perliedman/leaflet-underneath">Leaflet Underneath</a>
		</td><td>
			使用Mapbox矢量瓦片数据查找某个地点附近的有趣要素（feature），并在速度和带宽有限的情况下为瓦片层添加互动功能。
		</td><td>
			<a href="http://github.com/perliedman">Per Liedman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/utahemre/Leaflet.GeoJSONAutocomplete">Leaflet.GeoJSONAutocomplete</a>
		</td><td>
			使用 GeoJSON 服务自动进行远程搜索的 Leaflet 插件。
		</td><td>
			<a href="https://github.com/utahemre">Yunus Emre Özkaya</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/maydemirx/leaflet-tag-filter-button">L.tagFilterButton</a>
		</td><td>
			通过标签过滤 LeafLet 标记
		</td><td>
			<a href="https://github.com/maydemirx">Mehmet Aydemir</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Twista/leaflet-google-places-autocomplete">Leaflet-gplaces-autocomplete</a>
		</td><td>
			在地图中添加谷歌地点搜索
		</td><td>
			<a href="https://github.com/Twista">Michal Haták</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yafred/leaflet-responsive-popup">leaflet-responsive-popup</a>
		</td><td>
			无需移动地图即可看到弹出窗口的内容。
		</td><td>
			<a href="https://github.com/yafred">YaFred</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/slutske22/leaflet-popup-modifier">leaflet-popup-modifier</a>
		</td><td>
			允许用户编辑弹出窗口的内容，或使用弹出窗口删除其源标记。
		</td><td>
			<a href="https://github.com/slutske22">Slutske22</a>
		</td>
	</tr>
</table>



### Area/overlay selection

这些插件帮助用户选择地图中的覆盖层或区域。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/heyman/leaflet-areaselect/">Leaflet.AreaSelect</a>
		</td><td>
			一个固定位置的、可调整大小的矩形，用于选择地图上的一个区域。
		</td><td>
			<a href="http://heyman.info">Jonatan Heyman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/kajic/leaflet-locationfilter/">leaflet-locationfilter</a>
		</td><td>
			一个可拖动/可调整大小的矩形，用于选择地图上的一个区域。
		</td><td>
			<a href="https://github.com/kajic">Robert Kajic</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/w8r/L.Control.LineStringSelect">L.Control.LineStringSelect</a>
		</td>
		<td>
			Fast LineString(polyline) 部分选择工具：选择复杂路径中两点之间的一段路径 <a href="https://w8r.github.io/L.Control.LineStringSelect">Demo</a>
		</td>
		<td>
			<a href="https://github.com/w8r">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/openplans/Leaflet.FeatureSelect">Leaflet.FeatureSelect</a>
		</td><td>使用可配置的中心点标记从 GeoJSON 图层中选择任何几何类型。
		</td><td>
			<a href="https://github.com/atogle">Aaron Ogle</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-geojson-selector">Leaflet GeoJSON Selector</a>
		</td>
		<td>
			用于在交互式列表和地图中选择 GeoJSON 要素（feature）的 Leaflet 控件 (<a href="http://labs.easyblog.it/maps/leaflet-geojson-selector/">Demo</a>)
		</td>
		<td>
			<a href="http://labs.easyblog.it/stefano-cudini/">Stefano Cudini</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IvanSanchez/Leaflet.CheapLayerAt">Leaflet.CheapLayerAt</a>
		</td>
		<td>
			允许查询屏幕坐标下的图层 (<a href="http://ivansanchez.github.io/Leaflet.CheapLayerAt/demo.html">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sandropibia/Leaflet.SelectAreaFeature/">Leaflet.SelectAreaFeature</a>
		</td><td>
			通过绘制区域来选择地图上的要素图层。
		</td><td>
			<a href="http://pezzo.org">Sandro Pibia</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mkong0216/leaflet-shades/"> Leaflet-Shades </a>
		</td>
		<td>
			一个可拖动和可调整大小的矩形，用于在地图上选择一个区域并在未选择的区域中创建一个灰色叠加图层 (<a href="https://mkong0216.github.io/leaflet-shades/examples">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/mkong0216"> Mandy Kong </a>
		</td>
	</tr>
  <tr>
		<td>
			<a href="https://github.com/zakjan/leaflet-lasso">leaflet-lasso</a>
		</td>
		<td>
			真正的套索选择插件 (<a href="http://zakjan.github.io/leaflet-lasso/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/zakjan">Jan Zak</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/olanaso/Leaflet-Select-Polygons">Leaflet-Select-Polygons</a>
		</td>
		<td>
			Leaflet-Select-Polygons 允许选择多个多边形并调整基本地图视图 (<a href="https://olanaso.github.io/Leaflet-Select-Polygons/">demo</a>)
		</td>
		<td>
			<a href="https://github.com/olanaso">Erick S Escalante Olano</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bopen/leaflet-area-selection">@bopen/leaflet-area-selection</a>
		</td>
		<td>
			leaflet-area-selection allows to easily select a polygonal area on the map (see the <a href="https://bopen.github.io/leaflet-area-selection/">demo</a>)
		</td>
		<td>
			<a href="https://www.bopen.eu/">B-Open</a>
		</td>
	</tr>
</table>



## 地图交互

与地图本身交互的新方法。

* [控制图层切换](#layer-switching-controls)
* [交互式平移/缩放](#interactive-panzoom)
* [带书签的平移/缩放](#bookmarked-panzoom)
* [全屏](#fullscreen-controls)
* [小地图 & 同步地图](#minimaps--synced-maps)
* [测量](#measurement)
* [鼠标坐标](#mouse-coordinates)
* [事件](#events)
* [用户界面](#user-interface)
* [打印/导出](#printexport)
* [地理位置](#geolocation)

### Layer switching controls

以下插件用于增强或扩展 `L.Control.Layers`。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/aebadirad/Leaflet.AutoLayers">Leaflet.AutoLayers</a>
		</td><td>
			自动从多个地图服务器中提取图层，并通过用户控制的覆盖图层的 zIndex 管理组织/搜索它们。
		</td><td>
			<a href="https://github.com/aebadirad">Alex Ebadirad</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/vogdb/SelectLayersControl">Leaflet.SelectLayers</a>
		</td><td>
			一个Leaflet插件，它增加了新的控件来切换地图上的不同图层。新控件用选择标签取代了 L.Control.Layers 单选按钮面板。
		</td><td>
			<a href="https://github.com/vogdb">vogdb</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/davicustodio/Leaflet.StyledLayerControl">Leaflet.StyledLayerControl</a>
		</td><td>
			一个 Leaflet 插件，通过组织成 style 或 group 来实现对层的管理和控制。
		</td><td>
			<a href="https://github.com/davicustodio">Davi Custodio</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ismyrnow/Leaflet.groupedlayercontrol">Leaflet.GroupedLayerControl</a>
		</td><td>
            Leaflet 图层控件，支持将叠加组合在一起。
		</td><td>
			<a href="https://github.com/ismyrnow">Ishmael Smyrnow</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://elesdoar.github.io/leaflet-control-orderlayers/">Leaflet Control Order Layers</a>
		</td><td>
			增加了在图层控件中改变叠加顺序的能力。
		</td><td>
			<a href="https://github.com/elesdoar/">Michael Salgado</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/robbiet480/leaflet-categorized-layers">Leaflet Categorized Layers</a>
		</td><td>
			Leaflet 的控制图层（Control Layers）扩展为分类图层组（groups of categorized layers） 
		</td><td>
			<a href="http://robbie.io/">Robbie Trencheny</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-panel-layers">Leaflet Panel Layers</a>
		</td><td>
			Leaflet 控制图层扩展为图层组（group of layers）和图标图例（icons legend）
		</td><td>
			<a href="http://labs.easyblog.it">Stefano Cudini</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/chriscalip/L.UniformControl">Leaflet.UniformControl</a>
		</td><td>
			带有样式复选框和单选按钮的 Leaflet 图层控件。
		</td><td>
			<a href="https://github.com/chriscalip">Chris Calip</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ScanEx/Leaflet-IconLayers">Leaflet-IconLayers</a>
		</td><td>
			将基础层显示为小图标的 Leaflet 控件 (<a href="http://scanex.github.io/Leaflet-IconLayers/examples">demo</a>)
		</td><td>
			<a href="https://github.com/zverev">Alexander Zverev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bambrikii/leaflet-layer-tree-plugin">Leaflet.LayerTreePlugin</a>
		</td><td>
			Leaflet 控件允许打开和关闭图层，并以树状方式显示它们 (<a href="http://rawgit.com/bambrikii/leaflet-layer-tree-plugin/master/examples/basic-example.htm">demo</a>)
		</td><td>
			<a href="https://github.com/bambrikii">Alexander Arakelyan</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/consbio/Leaflet.Basemaps">Leaflet.Basemaps</a>
		</td><td>
			带有来自瓦片堆栈的预览图像的底图选择器
			<a href="http://consbio.github.io/Leaflet.Basemaps/">示例</a>
		</td><td>
			<a href="https://github.com/brendan-ward">Brendan Ward</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jjimenezshaw/Leaflet.Control.Layers.Tree">Leaflet.Control.Layers.Tree</a>
		</td><td>
            L.Control.Layers 扩展支持树结构，适用于基础层和覆盖层。简单且高度可配置。查看 <a href="https://jjimenezshaw.github.io/Leaflet.Control.Layers.Tree/examples/">demos</a>
		</td><td>
			<a href="https://github.com/jjimenezshaw/">Javier Jimenez Shaw</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/vogdb/Leaflet.ActiveLayers">Leaflet.ActiveLayers</a>
		</td><td>
			添加新的 L.Control.ActiveLayers，具有在地图上获取当前活动图层的功能。
		</td><td>
			<a href="https://github.com/vogdb">vogdb</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Kanahiro/Leaflet.Control.Appearance">Leaflet.Control.Appearance</a>
		</td><td>
			Control.Layers 的扩展，可以控制图层的外观 - 颜色、不透明度并能够删除叠加层 <a href="https://github.com/Kanahiro/Leaflet.Control.Appearance">示例</a>
		</td><td>
			<a href="https://www.labo288.site/">Kanahiro Iguchi</a>
		</td>
	</tr>
</table>


### Interactive pan/zoom

改变用户在地图上交互移动的方式。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="http://kartena.github.com/Leaflet.Pancontrol/">Leaflet.Pancontrol</a>
		</td><td>
			一个简单的平移控件。
		</td><td>
			<a href="http://www.kartena.se/">Kartena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gregallensworth/L.Control.BoxZoom">Leaflet.BoxZoom</a>
		</td><td>
			一个可见的、可点击的控件，用于执行框缩放。
		</td><td>
			<a href="https://github.com/gregallensworth/L.Control.BoxZoom">Greg Allensworth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/elrobis/L.Control.ZoomBar">L.Control.ZoomBar</a>
		</td><td>
			Leaflet 原生 Zoom 控件的扩展版本，带有 Home 和 Zoom-to-Area 按钮。 <a href="https://elrobis.github.io/L.Control.ZoomBar/">Demo</a>
		</td><td>
			<a href="http://cartometric.com/blog/">Elijah Robison</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://kartena.github.com/Leaflet.zoomslider/">Leaflet.zoomslider</a>
		</td><td>
			缩放滑块控件。
		</td><td>
			<a href="http://www.kartena.se/">Kartena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/flaviocarmo/Leaflet.zoominfo/">Leaflet.zoominfo</a>
		</td><td>
			显示当前缩放级别的缩放控件。
		</td><td>
			<a href="https://github.com/flaviocarmo">Flávio Carmo</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/slara/Leaflet.BorderPan">Leaflet.BorderPan</a>
		</td><td>
			通过单击地图边框进行平移的 Leaflet 插件。
		</td><td>
			<a href="https://github.com/slara">Sebastián Lara</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/SINTEF-9012/Leaflet.GameController">Leaflet GameController</a>
		</td><td>
			为游戏手柄提供支持的交互处理程序。
		</td><td>
			<a href="https://github.com/yellowiscool">Antoine Pultier</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/aratcliffe/Leaflet.twofingerzoom">Leaflet.twofingerZoom</a>
		</td><td>
			 用于触摸设备的交互处理程序，可通过两指轻敲来缩小。
		</td><td>
			<a href="https://github.com/aratcliffe/">Adam Ratcliffe</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/consbio/Leaflet.ZoomBox">Leaflet.ZoomBox</a>
		</td>
		<td>
			轻量级缩放框控件：在要缩放到的区域周围绘制一个框。 <a href="https://consbio.github.io/Leaflet.ZoomBox">Demo</a>
		</td>
		<td>
			<a href="https://github.com/brendan-ward">Brendan Ward</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Zverik/Leaflet.LimitZoom">Leaflet LimitZoom</a>
		</td><td>
			通过限制缩放或插入图块来将可用缩放级别限制为给定列表的插件。
		</td><td>
			<a href="https://github.com/zverik">Ilya Zverev</a>
		</td>
	</tr>
  <tr>
		<td>
			<a href="https://github.com/GhostGroup/Leaflet.DoubleRightClickZoom">Leaflet.DoubleRightClickZoom</a>
		</td><td>
			启用双击鼠标右键缩小的交互处理程序。
		</td><td>
			<a href="https://github.com/mikeotoole/">Mike O'Toole</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/unbam/Leaflet.ZoomLabel">Leaflet.ZoomLabel</a>
		</td>
		<td>
			一个简单的缩放标签控件。
		</td>
		<td>
			<a href="https://github.com/unbam">Masashi Takeshita</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/will4906/leaflet.zoompanel">Leaflet.ZoomPanel</a>
		</td>
		<td>
			Leaflet 的缩放控制面板。 <a href="https://will4906.github.io/leaflet-zoompanel/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/will4906/">Shuhua Huang</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/petoc/Leaflet.DoubleTouchDragZoom">Leaflet.DoubleTouchDragZoom</a>
		</td>
		<td>
			Plugin for one finger zoom. <a href="https://petoc.github.io/Leaflet.DoubleTouchDragZoom/example/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/petoc">Peter C</a>
		</td>
	</tr>
</table>



### Bookmarked pan/zoom

通过跳转到预定义/存储的位置来改变用户在地图上移动的方式。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/pwldp/leaflet.viewcenter">Leaflet.viewcenter</a>
		</td><td>
			一个简单的控件，它添加了一个按钮来改变视图和缩放到选项中的预定义值。
		</td><td>
			<a href="https://github.com/pwldp/">Dariusz Pawlak</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/alanshaw/leaflet-zoom-min/">leaflet-zoom-min</a>
		</td><td>
			为缩放控制添加一个按钮，允许你在一次点击中缩放到地图的最小缩放级别。
		</td><td>
			<a href="https://github.com/alanshaw/">Alan Shaw</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/davidchouse/Leaflet.NavBar">Leaflet Navigation Toolbar</a>
		</td><td>
			用于简单后退、前进和主页导航的 Leaflet 控件。
		</td><td>
			<a href="https://github.com/davidchouse">David C</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mithron/leaflet.locationlist">Leaflet Locationlist</a>
		</td><td>
			用于在预定义位置和缩放之间跳转的控件。
		</td><td>
			<a href="https://github.com/mithron">Ivan Ignatyev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/nguyenning/Leaflet.defaultextent">Leaflet.defaultextent</a>
		</td>
		<td>
			一个可以返回到地图的原始起始范围的控件， 类似于 <a href="https://developers.arcgis.com/javascript/jssamples/widget_home.html">HomeButton</a> 小部件。
		</td>
		<td>
			<a href="https://github.com/nguyenning">Alex Nguyen</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/w8r/Leaflet.Bookmarks">Leaflet.Bookmarks</a>
		</td>
		<td>
			用于在地图上添加和导航用户创建的书签的控件。
		</td>
		<td>
			<a href="https://github.com/w8r/">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
        <td>
			<a href="https://github.com/florpor/Leaflet.ShowAll">Leaflet.ShowAll</a>
		</td><td>
			一个可以显示预定义范围的控件，同时保存当前的范围，以便可以跳回。
		</td><td>
			<a href="https://github.com/florpor">Mor Yariv</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/torfsen/leaflet.zoomhome">Leaflet.zoomhome</a>
		</td>
		<td>
			缩放控件，有一个用于重新设置视图的主按钮 (<a href="http://torfsen.github.io/leaflet.zoomhome/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/torfsen">Florian Brucker</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/cscott530/leaflet-history">Leaflet-History</a>
		</td>
		<td>
			类似于浏览器，跟踪地图移动和缩放位置的历史记录。
		</td>
		<td>
			<a href="https://github.com/cscott530">Chris Scott</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.RestoreView">Leaflet.RestoreView</a>
		</td><td>
			使用 localStorage 存储和恢复地图视图。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mlevans/leaflet-hash">leaflet-hash</a>
		</td><td>
			用于通过 URL 哈希持久保存地图状态和浏览历史的插件。
		</td><td>
			<a href="https://github.com/mlevans">Michael Lawrence Evans</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rwev/leaflet-view-meta">leaflet-view-meta</a>
		</td>
		<td>
			控制显示和持久化地图视图元数据，中心和边界坐标到URL的插件，以便精确共享和视图重建。
		</td>
		<td>
			<a href="https://github.com/rwev">rwev</a>
		</td>
	</tr>
</table>



### Fullscreen controls

允许以全屏模式显示地图。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/mapbox/Leaflet.fullscreen">Leaflet.fullscreen</a>
		</td><td>
			一个由 Mapbox 提供的全屏按钮控件
		</td><td>
			<a href="https://github.com/mapbox">Mapbox</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://brunob.github.com/leaflet.fullscreen">leaflet.fullscreen</a>
		</td><td>
			另一个全屏按钮控件，但适用于现代浏览器，使用 HTML5 全屏 API。
		</td><td>
			<a href="https://github.com/brunob/">Bruno B</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://elidupuis.github.com/leaflet.zoomfs">leaflet.zoomfs</a>
		</td><td>
			全屏按钮控件。
		</td><td>
			<a href="https://github.com/elidupuis">Eli Dupuis</a>
		</td>
	</tr>
</table>



### Minimaps & synced maps

同时显示两张地图。其中一个可能是不同的尺寸和缩放级别，可作为最小地图使用，以帮助用户进行导航。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/turban/Leaflet.Sync">Leaflet.Sync</a>
		</td><td>
			两张地图的同步视图。
		</td><td>
			<a href="https://github.com/turban">Bjørn Sandvik</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Norkart/Leaflet-MiniMap">Leaflet.MiniMap</a>
		</td><td>
			一个以不同的比例尺显示的迷你地图，以帮助导航。
		</td><td>
			<a href="https://github.com/robpvn">Robert Nordan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bbecquet/Leaflet.MagnifyingGlass">Leaflet.MagnifyingGlass</a>
		</td><td>
			允许你在另一个缩放级别上显示地图的一小部分，可以在一个固定的位置，也可以与鼠标移动相联系，以达到放大镜的效果。
		</td><td>
			<a href="https://github.com/bbecquet/">Benjamin Becquet</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jieter/Leaflet.layerscontrol-minimap">Leaflet.layerscontrol-minimap</a>
		</td><td>
			用同步的迷你地图扩展默认的 Leaflet layers control。
		</td><td>
			<a href="https://github.com/jieter">Jieter</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/chriswhong/leaflet-globeminimap/">Leaflet.GlobeMiniMap</a>
		</td><td>
			简单的小地图控件，以与主地图相同的位置为中心将 3D 地球仪放置在地图的角落 (<a href='http://chriswhong.github.io/leaflet-globeminimap/example/'>demo</a>)
		</td><td>
			<a href="https://github.com/chriswhong">Chris Whong</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jieter/leaflet-clonelayer">leaflet-clonelayer</a>
		</td><td>
			克隆 Leaflet 图层，以允许在同一运行时间内的不同地图中重复使用。
		</td><td>
			<a href="https://github.com/jieter">Jieter</a>
		</td>
	</tr>
</table>






### Measurement

允许用户测量距离或面积。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/ppete2/Leaflet.PolylineMeasure">Leaflet.PolylineMeasure</a>
		</td><td>
			测量简单的线和复杂的折线的大圆距离。 (<a href="https://ppete2.github.io/Leaflet.PolylineMeasure/demo1.html">Demo 1</a>), (<a href="https://ppete2.github.io/Leaflet.PolylineMeasure/demo2.html">Demo 2</a>), (<a href="https://ppete2.github.io/Leaflet.PolylineMeasure/demo3.html">Demo 3</a>)
		</td><td>
			<a href="https://github.com/ppete2">PPete</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.MeasureControl">Leaflet.MeasureControl</a>
		</td><td>
			在地图上测量距离的简单工具（依赖于 Leaflet.Draw）。
		</td><td>
			<a href="https://github.com/makinacorpus/">Makina Corpus</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/zvaraondrej/Leaflet.MeasureAreaControl">Leaflet.MeasureAreaControl</a>
		</td><td>
			测量元素面积的控件。 
		</td><td>
			<a href="https://github.com/zvaraondrej">Ondrej Zvara</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ljagis/leaflet-measure">leaflet-measure</a>
		</td>
		<td>
			Leaflet 地图的坐标、线和面积测量控件
		</td>
		<td>
			<a href="https://github.com/ljagis">LJA GIS</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/nerik/leaflet-graphicscale">leaflet-graphicscale</a>
		</td>
		<td>
			控制动画的图形比例 (<a href='http://nerik.github.io/leaflet-graphicscale/demo/'>demo</a>)
		</td>
		<td>
			<a href="https://github.com/nerik">Erik Escoffier</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MarcChasse/leaflet.ScaleFactor">Leaflet.ScaleFactor</a>
		</td><td>
			显示 Leaflet 地图的比例（例如 1:50,000） (<a href="https://marcchasse.github.io/leaflet.ScaleFactor/">Demo</a>)
		</td><td>
			<a href="https://github.com/MarcChasse">Marc Chasse</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/PowerPan/leaflet.nauticscale">Leaflet.nauticscale</a>
		</td><td>
			在 Leaflet 地图上显示 Nauticscale
		</td><td>
			<a href="https://github.com/PowerPan">Johannes Rudolph</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ProminentEdge/leaflet-measure-path">Leaflet Measure Path</a>
		</td><td>
			显示路径上的测量值；目前支持折线、多边形和圆。 (<a href="http://prominentedge.com/leaflet-measure-path/">demo</a>)
		</td><td>
			<a href="https://github.com/perliedman">Per Liedman</a> / <a href="http://prominentedge.com/">Prominent Edge</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/NLTGit/Leaflet.LinearMeasurement">Leaflet.LinearMeasurement</a>
		</td><td>
			Leaflet 线性测量插件，可创建沿路径增量测量的折线。 (<a href="https://nltgit.github.io/Leaflet.LinearMeasurement/">demo</a>)
		</td><td>
			<a href="http://www.newlighttechnologies.com/">New Light Technologies</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gokertanrisever/leaflet-ruler">leaflet-ruler</a>
		</td><td>
			一个简单的 Leaflet 插件，用于测量真实方位和点击的位置之间的距离。 (<a href="https://gokertanrisever.github.io/leaflet-ruler/">Demo</a>)
		</td><td>
			<a href="https://github.com/gokertanrisever">Goker Tanrisever</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rwev/leaflet-reticle">leaflet-reticle</a>
		</td>
		<td>
			Leaflet 控件，添加了一个由独立计算的纬度和经度刻度组成的居中标线。
		</td>
		<td>
			<a href="https://github.com/rwev">rwev</a>
		</td>
	</tr>
	
</table>








### Mouse coordinates

以不同方式显示鼠标光标下的地理坐标。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/ardhi/Leaflet.MousePosition">Leaflet.MousePosition</a>
		</td><td>
			一个简单的 MousePosition 控件，显示鼠标指针在地图上移动时的地理坐标
		</td><td>
			<a href="https://github.com/ardhi">Ardhi Lukianto</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/YUUKIToriyama/Leaflet.MousePosition.ts">Leaflet.MousePosition.ts</a>
		</td><td>
			A fully custmizable coordinate viewer written in TypeScript.
			You can change how this plugin looks by creating a custom component with JSX.
			(<a href="https://yuukitoriyama.github.io/Leaflet.MousePosition.ts">demo</a>)
		</td><td>
			<a href="https://github.com/YUUKIToriyama">Yuuki Toriyama</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MrMufflon/Leaflet.Coordinates">Leaflet.Coordinates</a>
		</td><td>
			一个简单的Leaflet插件，用于查看鼠标的 LatLng-coordinates，也可以在用户输入时查看一个带有坐标弹出的标记。
		</td><td>
			<a href="https://github.com/MrMufflon">Felix Bache</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/zimmicz/Leaflet-Coordinates-Control">Leaflet Coordinates Control</a>
		</td><td>
			捕捉鼠标点击并显示其坐标，并且可以轻松复制它们。
		</td><td>
			<a href="https://github.com/zimmicz">Michal Zimmermann</a>
		</td>
	</tr>
    	<tr>
		<td>
			<a href="https://github.com/tinjaw/Leaflet-Copy-Coordinates-Control">Leaflet Copy Coordinates Control</a>
		</td><td>
			与 Leaflet 一起使用来捕获地图上的鼠标点击，并以一种简单的方式复制它们来显示关联的坐标。（源自 zimmicz 的原创作品，分支主要是为了提供 npm 功能。）
		</td><td>
			<a href="https://github.com/tinjaw">Chaim Krause</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mahmoodvcs/Leaflet.NACCoordinates">Leaflet.NACCoordinates</a>
		</td>
		<td>
			在鼠标移动时显示鼠标指针的 NAC 坐标 (<a href="http://mahmoodvcs.github.io/Leaflet.NACCoordinates/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/mahmoodvcs">Mahmood Dehghan</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/PowerPan/leaflet.mouseCoordinate">Leaflet.mouseCoordinates</a>
		</td>
		<td>
			在一个方框中可采用多种格式来显示鼠标坐标。
			<ul>
				<li>GPS</li>
				<li>UTM</li>
				<li>UTMREF / MGRS</li>
				<li>QTH</li>
			</ul>
		</td>
		<td>
			<a href="https://github.com/PowerPan">Johannes Rudolph</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-locationpicker">Leaflet Location Picker</a>
		</td>
		<td>
			简单的并且带有迷你 Leaflet 地图的位置选择器 (<a href="http://labs.easyblog.it/maps/leaflet-locationpicker/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/stefanocudini/">Stefano Cudini</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/xguaita/Leaflet.MapCenterCoord">Leaflet.MapCenterCoord</a>
		</td>
		<td>
			用于显示地图中心坐标的 Leaflet 控件，在触摸/移动设备上特别有用。(<a href="http://xguaita.github.io/Leaflet.MapCenterCoord/">Doc & demos</a>)
		</td>
		<td>
			<a href="https://github.com/xguaita">Xisco Guaita</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/matlads/Leaflet.Mapcodes">Leaflet.Mapcodes</a>
		</td>
		<td>
			在鼠标移动时显示鼠标指针的 <a href="http://www.mapcode.com">Mapcode</a>  (<a href="http://matlads.github.io/Leaflet.Mapcodes/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/matlads">Martin Atukunda</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/edihasaj/leaflet-coord-projection">Leaflet.CoordProjection</a>
		</td>
		<td>
			Shows coordinates on mouse move and displays it based on given projection (<a href="https://edihasaj.github.io/leaflet-coord-projection/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/edihasaj">Edi Hasaj</a>
		</td>
	</tr>
</table>









### Events

这些插件扩展了 Leaflet 的事件处理的能力。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/elmarquis/Leaflet.GestureHandling/">Leaflet.GestureHandling</a>
		</td><td>
			将 Google 地图手势处理的基本功能带入 Leaflet。防止用户在滚动长页面时被困在地图上。<a href="https://elmarquis.github.io/Leaflet.GestureHandling/examples/"> Demo</a>
		</td><td>
			<a href="https://github.com/elmarquis">Andy Marquis</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/CliffCloud/Leaflet.Sleep">L.Sleep</a>
		</td><td>
			避免不必要的滚动捕获（capturing）事件。
			<a href="https://cliffcloud.github.io/Leaflet.Sleep"> Demo</a>
		</td><td>
			<a href="https://github.com/atstp">atstp</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.OverIntent">Leaflet.OverIntent</a>
		</td><td>
			添加一个新事件 “mouseintent”，它与 “mouseover” 不同，因为它反映了用户瞄准特定图层的意图。
		</td><td>
			<a href="https://github.com/makinacorpus/">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.AlmostOver">Leaflet.AlmostOver</a>
		</td><td>
			当光标 "几乎 "在一个图层上时触发鼠标事件。
		</td><td>
			<a href="https://github.com/makinacorpus/">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Mappy/Leaflet-active-area">Leaflet-active-area</a>
		</td><td>
			此插件允许您将地图的较小部分用作活动区域。所有定位方法（setView、fitBounds、setZoom）都将应用于此部分而不是所有地图。
		</td><td>
			<a href="https://github.com/Mappy">Mappy</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MazeMap/Leaflet.ControlledBounds">Leaflet.ControlledBounds</a>
		</td><td>
			受 Leaflet-active-area 的启发，自动检测地图上未被任何地图控件覆盖的最大区域，并将 setView、fitBounds、setZoom、getBounds 应用于该区域。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Outdooractive/leaflet-singleclick_0.7">singleclick</a>
		</td>
		<td>
			扩展 L.Map 以触发 singleclick 事件（<a href="http://outdooractive.github.io/leaflet-singleclick_0.7/">demo</a>）。仅与 Leaflet 0.7.x 兼容。
		</td>
		<td>
			<a href="http://glat.info">Guillaume Lathoud</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MazeMap/Leaflet.singleclick">singleclick</a>
		</td>
		<td>
			扩展 L.Evented 以触发 singleclick 事件（<a href="https://mazemap.github.io/Leaflet.singleclick/">demo</a>）。仅与 Leaflet 1.0.0-beta1 及更高版本兼容。
		</td><td>
			<a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
			<a href="https://github.com/MazeMap">MazeMap</a>
		</td>
	</tr>
	<tr>
	        <td>
	            <a href="https://github.com/MazeMap/Leaflet.VisualClick">Leaflet.VisualClick</a>
	        </td>
	        <td>
	            当用户点击/点击地图时添加视觉反馈（<a href="https://github.com/MazeMap/Leaflet.VisualClick/">demo</a>）。当服务器请求或 Leaflet.singleclick 的实现延迟进一步操作时很有用，或者只是因为它看起来很酷:) 仅在 Leaflet 1.0.0-beta1 测试过。
	        </td><td>
	            <a href="https://github.com/dagjomar">Dag Jomar Mersland</a>,
	            <a href="https://github.com/IvanSanchez">Iván Sánchez Ortega</a>,
	            <a href="https://github.com/MazeMap">MazeMap</a>
	        </td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/perliedman/leaflet-touch-helper">Leaflet Touch Helper</a>
		</td><td>
			通过添加透明、更大的触摸表面，可以轻松地在小显示屏上用粗手指触摸矢量叠加层
		</td><td>
			<a href="https://github.com/perliedman">Per Liedman</a> / <a href="http://prominentedge.com/">Prominent Edge</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/geoloep/Leaflet.ClickTolerance">Leaflet.ClickTolerance</a>
		</td><td>
			该插件允许您增加画布驱动层的点击容差，从而可以增加矢量图层的可点击区域超出其可见范围。当您的功能难以点击时很有用。
		</td><td>
			<a href="https://github.com/geoloep">Geoloep</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/idawave/Leaflet.DraggableEnhancer">L.DraggableEnhancer</a>
		</td><td>
			例如，如果地图容器的父级之一具有附加到 “mousemove” 事件的预定义处理程序（如“event.stopPropagation()”），则修改默认的 L.Draggable 处理程序（负责地图平移，...）以使其正常工作。
		</td><td>
			<a href="https://github.com/idawave">Vincent Dechandon</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iboates/leaflet-spotlight">L.Spotlight</a>
		</td><td>
			使用可自定义的形状动态突出显示鼠标光标附近的元素（feature）
		</td><td>
			<a href="https://github.com/iboates">Isaac Boates</a>
		</td>
	</tr>
</table>



### User interface

按钮、滑块、工具栏、侧边栏和面板。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/yigityuce/Leaflet.Control.Custom">Leaflet.Control.Custom</a>
		</td><td>
			完全可定制的带有 HTML 元素的 Leaflet 控制面板。
			<a href="https://yigityuce.github.io/Leaflet.Control.Custom/examples/index.html"> Demo</a>
		</td><td>
			<a href="https://github.com/yigityuce">Yiğit Yüce</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/CliffCloud/Leaflet.EasyButton">L.EasyButton</a>
		</td><td>
			在一行中，添加一个带有点击事件的 Font Awesome 控件按钮。
			<a href="https://cliffcloud.github.io/Leaflet.EasyButton"> Demo</a>
		</td><td>
			<a href="https://github.com/atstp">atstp</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/aratcliffe/Leaflet.contextmenu">Leaflet.contextmenu</a>
		</td><td>
			Leaflet 的 contextmenu 菜单。
		</td><td>
			<a href="https://github.com/aratcliffe/">Adam Ratcliffe</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/ahalota/Leaflet.CountrySelect/">Leaflet.CountrySelect</a>
		</td><td>
			控制所有国家/地区的菜单，以及将所选国家/地区作为 GeoJSON 功能返回的事件侦听器 (<a href="http://ahalota.github.io/Leaflet.CountrySelect/demo.html">demo</a>)
		</td><td>
			<a href="https://github.com/ahalota/">Anika Halota</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/easymountain/Leaflet.GeojsonLayerSwitcher">Leaflet.GeojsonLayerSwitcher</a>
		</td>
		<td>
			允许在GeoJSON层之间导航，选择一些，并返回选择。
		</td>
		<td>
			<a href="https://github.com/easymountain">Easy-Mountain</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/nickpeihl/leaflet-sidebar-v2/">leaflet-sidebar-v2</a>
		</td><td>
			带有 HTML 和 JS API 的响应式标签式侧边栏。与旧的 (0.7) 和当前的 Leaflet 兼容。
		</td><td>
			<a href="https://github.com/noerw/">Norwin Roosen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/turbo87/leaflet-sidebar/">leaflet-sidebar</a>
		</td><td>
			响应式侧边栏插件。
		</td><td>
			<a href="https://github.com/turbo87/">Tobias Bieniek</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/turbo87/sidebar-v2/">sidebar-v2</a>
		</td><td>
			另一个响应式侧边栏插件。这次带有标签！
		</td><td>
			<a href="https://github.com/turbo87/">Tobias Bieniek</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tinuzz/leaflet-messagebox">Leaflet.Messagebox</a>
		</td>
		<td>
			在地图上显示临时文本消息 (<a href="https://www.grendelman.net/leaflet/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/tinuzz/">Martijn Grendelman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://gitlab.com/manuel.richter95/leaflet.notifications">Leaflet.Notifications</a>
		</td>
		<td>
			Spawn toast notifications inside your map
		</td>
		<td>
			<a href="https://gitlab.com/manuel.richter95">Manuel Richter</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.TileLegend">Leaflet.TileLegend</a>
		</td><td>
			为您的背景图层创建插图和交互式图例。
		</td><td>
			<a href="http://yohanboniface.me">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Leaflet/Leaflet.toolbar">Leaflet.toolbar</a>
		</td>
		<td>
			用于 Leaflet 地图的灵活、可扩展的工具条。在<a href="https://leaflet.github.io/Leaflet.toolbar/examples/popup.html">此处</a>查看示例。
		</td>
		<td>
			<a href="https://github.com/manleyjster">Justin Manley</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gregallensworth/L.Control.Credits">L.Credits</a>
		</td>
		<td>
			一个简单、有吸引力的交互式控件，可将您的徽标和链接放在地图的角落。
		</td>
		<td>
			<a href="https://github.com/gregallensworth/">Greg Allensworth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.Spin">Leaflet.Spin</a>
		</td><td>
			使用 <a href="http://fgnass.github.com/spin.js/">Spin.js</a> 在地图上显示一个漂亮的微调器，用于异步数据加载，就像使用 <a href="https://github.com/calvinmetcalf/leaflet-ajax">Leaflet Ajax</a> 一样。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/oskosk/Leaflet.Weather">Leaflet Weather</a>
		</td>
		<td>
			一个 Leaflet 插件，用于使用 OpenWeatherMap API 在地图上添加一个天气小部件。 (<a href="http://oskosk.github.io/Leaflet.Weather/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/oskosk">Osk</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dalbrx/Leaflet.ResizableControl">Leaflet ResizableControl</a>
		</td>
		<td>
			一个 Leaflet 插件，在地图上添加一个可调整大小和可滚动的控件。 (<a href="http://dalbrx.github.io/Leaflet.ResizableControl/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/dalbrx">David Albrecht</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Eclipse1979/leaflet-slider">Leaflet.Slider</a>
		</td>
		<td>
			添加一个<code>&lt;input type="range"&gt;</code>滑块，每次改变其输入都会调用一个函数。 (<a href="https://github.com/Eclipse1979/leaflet-slider">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/Eclipse1979">EPP</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapshakers/leaflet-control-window">leaflet-control-window</a>
		</td><td>
		    在你的地图中创建模态/无模态、可拖动、可响应、可定制的窗口。
		</td><td>
			<a href="https://github.com/mapshakers">mapshakers</a>/
			<a href="https://github.com/filipzava">Filip Zavadil</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/utahemre/Leaflet.CoordinatedImagePreview">Leaflet.CoordinatedImagePreview</a>
		</td><td>
			在地图范围内显示协调的图像。
		</td><td>
			<a href="https://github.com/utahemre">Yunus Emre Özkaya</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/unbam/Leaflet.SlideMenu">Leaflet.SlideMenu</a>
		</td>
		<td>
			一个用于Leaflet的简单的滑动菜单。
		</td>
		<td>
			<a href="https://github.com/unbam">Masashi Takeshita</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/NBTSolutions/Leaflet.Dialog">Leaflet.Dialog</a>
		</td>
		<td>
			一个简单的可调整大小、可移动、可自定义的对话框。 (<a href="http://nbtsolutions.github.io/Leaflet.Dialog/">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/NBTSolutions">NBT Solutions</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/MAD-GooZe/Leaflet.BootstrapZoom">Leaflet.BootstrapZoom</a>
		</td>
		<td>
			使用 Twitter Bootstrap 样式的按钮覆盖默认的缩放控制按钮
		</td>
		<td>
			<a href="https://github.com/MAD-GooZe">Alexey Gusev</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/route360/Leaflet.CondensedAttribution">Leaflet.CondensedAttribution</a>
		</td>
		<td>
			一个能使长属性在悬停时可见的属性插件
		</td>
		<td>
			<a href="http://www.motionintelligence.net/">Motion Intelligence GmbH</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/consbio/Leaflet.HtmlLegend">Leaflet.HtmlLegend</a>
		</td>
		<td>
			一个简单的 Leaflet 插件，用于使用 HTML 元素创建图例。 <a href="https://consbio.github.io/Leaflet.HtmlLegend/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/ka7eh">Kaveh Karimi</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/publiclab/leaflet-blurred-location/">leaflet-blurred-location</a>
		</td>
		<td>
			一个基于 Leaflet 的界面，用于选择一个 "模糊 "或低分辨率的位置，以保护隐私。 <a href="https://publiclab.github.io/leaflet-blurred-location/examples/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/publiclab">Public Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jjimenezshaw/Leaflet.Control.Resizer">Leaflet.Control.Resizer</a>
		</td><td>
			在右侧或底部控制调整你的地图大小。 查看 <a href="https://jjimenezshaw.github.io/Leaflet.Control.Resizer/examples/basic.html">demo</a>
		</td><td>
			<a href="https://github.com/jjimenezshaw/">Javier Jimenez Shaw</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/publiclab/leaflet-blurred-location-display">leaflet-blurred-location-display
			</a>
		</td>
		<td>
			在从远程API获取数据时，巧妙地使用彩色编码的热图和彩色编码的标记来分配 "模糊的 "位置 <a href="https://publiclab.github.io/leaflet-blurred-location-display/examples/HumanReadableBlurring.html">Demo</a>
		</td>
		<td>
			<a href="https://github.com/publiclab">Public Lab</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/ptma/Leaflet.Legend">Leaflet.Legend
			</a>
		</td>
		<td>
			显示图例符号和切换覆盖物 (<a href="https://ptma.github.io/Leaflet.Legend/examples/legend.html">Demo</a>)
		</td>
		<td>
			<a href="https://github.com/ptma">JJ Jin</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/adammertel/Leaflet.Control.Select">Leaflet.Control.Select
			</a>
		</td>
		<td>
			Customisable menu-style control. See <a href="https://adammertel.github.io/Leaflet.Control.Select/">demo</a>.
		</td>
		<td>
			<a href="https://github.com/adammertel">Adam Mertel</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/williamlow/Leaflet.Signposts">Leaflet.Signposts
			</a>
		</td>
		<td>
			Guides users to points outside the current map view with directional arrows and a count of points in each given direction. See <a href="https://williamlow.github.io/leaflet-signpost/demo.html">demo</a>.
		</td>
		<td>
			<a href="https://github.com/williamlow">William Low</a>
		</td>
	</tr>	
</table>



### Print/export

打印或导出你的地图。

<!--
- Saving a Leaflet Map to a PNG Example using Javascript and PHP https://github.com/tegansnyder/Leaflet-Save-Map-to-PNG
- Get a PNG from a Leaflet map and export it in PDF https://github.com/chrissom/leaflet-pdf
-->

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/aratcliffe/Leaflet.print">Leaflet.print</a>
		</td><td>
			实现 Mapfish 打印协议，允许使用 Mapfish 或 GeoServer 打印模块打印 Leaflet 地图。
		</td><td>
			<a href="https://github.com/aratcliffe">Adam Ratcliffe</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapbox/leaflet-image">Leaflet-image</a>
		</td><td>
			通过使用 Canvas 和 CORS，在没有服务器组件的情况下从 Leaflet 地图导出图像。
		</td><td>
			<a href="https://github.com/tmcw">Tom MacWright</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rowanwins/leaflet-easyPrint">Leaflet-easyPrint</a>
		</td><td>
			一个简单的插件，它添加了一个图标来打印你的 Leaflet 地图。
		</td><td>
			<a href="https://github.com/rowanwins">Rowan Winsemius</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Igor-Vladyka/leaflet.browser.print">leaflet.browser.print</a>
		</td><td>
			允许用户直接从浏览器打印整页地图。
		</td><td>
			<a href="https://github.com/Igor-Vladyka">Igor Vladyka</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/pasichnykvasyl/Leaflet.BigImage">Leaflet.BigImage</a>
		</td><td>
			允许用户下载带有放大版可见地图的图像。
		</td><td>
			<a href="https://github.com/pasichnykvasyl">Vasyl Pasichnyk (Oswald)</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/hersle/leaflet-route-print">leaflet-route-print</a>
		</td><td>
			Automatic PDF printing of routes (i.e. polylines) with custom scale, paper size and margin by covering the route with a sequence of identical rectangles.
		</td><td>
			<a href="https://github.com/hersle">Herman Sletmoen</a>
		</td>
	</tr>
</table>



### Geolocation

扩展 Leaflet 地理定位功能的插件。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/CliffCloud/Leaflet.LocationShare">L.LocationShare</a>
		</td><td>
			允许用户发送和接收带有消息的标记（marker）。
			<a href="https://cliffcloud.github.io/Leaflet.LocationShare"> Demo</a>
		</td><td>
			<a href="https://github.com/atstp">atstp</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/domoritz/leaflet-locatecontrol">Leaflet.Locate</a>
		</td><td>
			可定制的定位控件。
		</td><td>
			<a href="https://github.com/domoritz">Dominik Moritz</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/stefanocudini/leaflet-compass">Leaflet Control Compass</a>
		</td><td>
			一个用来构建简单的旋转罗盘的 Leaflet 控件
		</td><td>
			<a href="http://labs.easyblog.it/">Stefano Cudini</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/M165437/Leaflet.AccuratePosition">Leaflet.AccuratePosition</a>
		</td><td>
			Leaflet.AccuratePosition 主要为了提供一个理想精度的设备位置。
		</td><td>
			<a href="https://github.com/M165437">Michael Schmidt-Voigt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/rhlt/leaflet-geolet">Geolet</a>
		</td><td>
			A simple but highly customizable geolocation plugin for Leaflet
		</td><td>
			<a href="https://github.com/rhlt/">Ruben Holthuijsen</a>
		</td>
	</tr>
</table>





## 各种各样的



### Geoprocessing

以下插件可进行多种地理信息处理（点、线和多边形上的数学和拓扑操作）。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/kartena/Proj4Leaflet">Proj4Leaflet</a>
		</td><td>
			<a href="http://trac.osgeo.org/proj4js/">Proj4js</a> 集成插件，允许你在 Leaflet 中使用各种奇怪的投影。
		</td><td>
			<a href="http://www.kartena.se/">Kartena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/springmeyer/arc.js">arc.js</a>
		</td><td>
			一个可以与 Leaflet 一起使用的用于绘制大圆圈路线的 JS 库。
		</td><td>
			<a href="https://github.com/springmeyer">Dane Springmeyer</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tmcw/leaflet-pip">Leaflet-pip</a>
		</td><td>
			使用 <a href="https://github.com/substack/point-in-polygon">point-in-polygon</a> 进行简单的计算多边形中的点。
		</td><td>
			<a href="https://github.com/tmcw">Tom MacWright</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.GeometryUtil">Leaflet.GeometryUtil</a>
		</td><td>
			一组用于 Leaflet 几何形状的实用工具（线性参考等）。
		</td><td>
			<a href="https://github.com/bbecquet">Benjamin Becquet</a>, <a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/w8r/GreinerHormann">Greiner-Hormann</a>
		</td>
		<td>
			用于多边形裁剪和二元运算的 Greiner-Hormann 算法，适用于 Leaflet。
		</td>
		<td>
			<a href="https://github.com/w8r">Alexander Milevski</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/skeate/Leaflet.buffer">Leaflet.buffer</a>
		</td><td>
			使得用 Leaflet.draw 绘制的图形能够得到缓冲。
		</td><td>
			<a href="https://github.com/skeate">Jonathan Skeate</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/makinacorpus/Leaflet.LayerIndex">Leaflet.LayerIndex</a>
		</td><td>
			要素（feature）和图层的有效空间索引，使用 <a href="https://github.com/imbcmdth/RTree">RTree.js</a>。
		</td><td>
			<a href="https://github.com/leplatrem">Mathieu Leplatre</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mapzen/leaflet-spatial-prefix-tree">leaflet-spatial-prefix-tree</a>
		</td><td>
			用于可视化空间前缀树、四叉树和 geohash 的 Leaflet 插件。 查看 <a href="http://mapzen.github.io/leaflet-spatial-prefix-tree/">demo</a>
		</td><td>
			<a href="http://mapzen.com/">Mapzen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/jjimenezshaw/Leaflet.UTM">Leaflet.UTM</a>
		</td><td>
			将 L.LatLng 转换为 UTM（WGS84），反之亦然的简单方法，UTM字符串格式易于配置。它不依赖于任何其他或第三方插件。 查看 <a href="https://jjimenezshaw.github.io/Leaflet.UTM/examples/input.html">demo</a>
		</td><td>
			<a href="https://github.com/jjimenezshaw/">Javier Jimenez Shaw</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/briannaAndCo/Leaflet.Antimeridian">Leaflet.Antimeridian</a>
		</td><td>
			一个插件，允许多边形和多段线自然地画过 Antimeridian（或国际日期线），而不是总是包裹在格林威治子午线上。 (<a href="https://briannaandco.github.io/Leaflet.Antimeridian/">Demo</a>)
		</td><td>
			<a href="https://github.com/briannaAndCo">Brianna Landon</a>
		</td>
	</tr>
</table>



### Routing

以下插件使用外部服务来计算驾驶或步行路线。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="http://www.liedman.net/leaflet-routing-machine/">Leaflet Routing Machine</a>
		</td><td>
            通过点控制路线搜索，显示行程和替代路线。默认使用 <a href="http://project-osrm.org/">OSRM</a> ，但也支持 <a href="https://graphhopper.com/">GraphHopper</a>、 <a href="https://www.mapbox.com/developers/api/directions/">Mapbox Directions API</a> 等。
		</td><td>
			<a href="https://github.com/perliedman">Per Liedman</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Turistforeningen/leaflet-routing">Leaflet.Routing</a>
		</td><td>
			使用任何用户提供的路由服务在航点之间路由路径的 Leaflet 控制器和接口。
		</td><td>
			<a href="https://github.com/turistforeningen">Norwegian Trekking Association</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/route360/r360-js">Route360°</a>
		</td><td>
			Route360°直观地显示了在给定时间内从一组起点可到达的区域，并提供了详细的路线信息（步行、自行车、汽车和<b>公共交通</b>）给目标。
		</td><td>
			<a href="http://www.motionintelligence.net/">Motion Intelligence GmbH</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/StephanGeorg/leaflet-routeboxer">Leaflet RouteBoxer</a>
		</td><td>
			这是来自 Google 的 RouteBoxer 类的 Leaflet 实现。Leaflet RouteBoxer 类生成一组 L.LatLngBounds 对象，这些对象保证覆盖路径指定距离内的每个点。
		</td><td>
			<a href="https://github.com/StephanGeorg">Stephan Georg</a>
		</td>
	</tr>
	<tr>
    		<td>
    			<a href="https://github.com/BKGiser/Leaflet.Routing.Amap">Leaflet.Routing.Amap</a>
    		</td><td>
		        使用<a href="http://www.amap.com/">AMap(高德地图)</a>作为后台进行路线搜索的控件。支持中国的BD09和GCJ02坐标系，彩色线条，以及弹出的转弯提示。
    		</td><td>
    			<a href="https://github.com/BKGiser">Jack Good</a>
    		</td>
    	</tr>

	<tr>
		<td>
			<a href="https://github.com/astridx/LeafletControlRouteToAddress">Leaflet RouteToAddress</a>
		</td><td>
			Control for route search from a custom address to a fixed address.
The Plugin integrates a simple geocoder that uses OpenstreetMap <a href="https://nominatim.openstreetmap.org/">Nominatim</a> to locate places by address. Ideal for the description of the directions "Find your way to us" on a website. Uses <a href="http://project-osrm.org/">OSRM</a> by default, but also supports
<a href="https://www.mapbox.com/developers/api/directions/">Mapbox Directions API</a>. <a href="https://astrid-guenther.de/dies-und-das/38-leaflet-control-plugin-leafletcontrolroutetoaddress/">Demo</a>
		</td><td>
			<a href="https://github.com/astridx/">Astrid Günther</a>
		</td>
	</tr>
    <tr>
    	<td>
    		<a href="https://github.com/skedgo/tripkit-leaflet">Leaflet TripGo routing</a>
    	</td>
    	<td>
    		<b>TripGo</b >移动平台让你创建应用程序，使用任何公共、私人或商业交通方式提供无缝和个性化的门到门旅行。
    		TripGo Leaflet 的插件动机是提供一种简单的方法，将其功能纳入外部平台。
    	</td>
    	<td>
    		<a href="http://skedgo.com/">SkedGo</a>
    	</td>
    </tr>
	<tr>
		<td>
			<a href="https://github.com/wwwouaiebe/leaflet.TravelNotes">leaflet.TravelNotes</a>
		</td>
		<td>
			Leaflet 的可编辑标记和路由引擎。路由引擎有 Mapbox、GraphHopper 和 OSRM 插件，可用于汽车、自行车或步行路线。 <a href="https://wwwouaiebe.github.io/leaflet.TravelNotes/?lng=en">Demo</a>
		</td>
		<td>
			<a href="https://github.com/wwwouaiebe">Christian Guyette</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/traffordDataLab/leaflet.reachability">Leaflet.Reachability</a>
		</td><td>
			使用 <a href="https://openrouteservice.org/documentation/#/reference/isochrones">openrouteservice isochrones API</a>，根据时间或距离显示不同旅行模式的可到达区域。
		</td><td>
			<a href="https://github.com/traffordDataLab">Trafford Data Lab</a>
		</td>
	</tr>
</table>




### Geocoding

将地址或地点名称转换为纬度和经度（反之亦然）的外部服务。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/smeijer/L.GeoSearch">Leaflet GeoSearch</a>
		</td><td>
            将地址搜索/查找（又名地理搜索）引入到 Leaflet 的小型地理编码插件。支持 Google、OpenStreetMap Nominatim、Bing、Esri 和诺基亚。易于扩展。
		</td><td>
			<a href="https://github.com/smeijer">Stephan Meijer</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/k4r573n/leaflet-control-osm-geocoder">Leaflet Control OSM Geocoder</a>
		</td><td>
			一个简单的地理编码器，它使用 OpenstreetMap Nominatim 按地址定位地点。
		</td><td>
			<a href="https://github.com/k4r573n">Karsten Hinz</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/sa3m/leaflet-control-bing-geocoder">Leaflet Control Bing Geocoder</a>
		</td><td>
			使用 Bing 定位地点的简单地理编码器控件。
		</td><td>
			<a href="https://github.com/sa3m">Samuel Piquet</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/perliedman/leaflet-control-geocoder">Leaflet Control Geocoder</a>
		</td><td>
			一个干净和可扩展的控件，用于地理编码和反向地理编码。内置支持 Nominatim, Bing, MapQuest, Mapbox, What3Words, Google 和 Photon。易于扩展到其他供应商。
		</td><td>
			<a href="https://github.com/perliedman">Per Liedman</a>
		</td>
	</tr>
    	<tr>
		<td>
			<a href="https://github.com/jakubdostal/leaflet-geoip">Leaflet GeoIP Locator</a>
		</td><td>
			一个简单的插件，可以找到 IP 地址的大致位置，并以所述位置为中心进行地图绘制。
		</td><td>
			<a href="https://github.com/jakubdostal">Jakub Dostal</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Esri/esri-leaflet-geocoder">Esri Leaflet Geocoder</a>
		</td><td>
			一个由 ArcGIS Online 地理编码器提供建议的地理编码控件。
		</td><td>
			<a href="https://github.com/patrickarlt/">Patrick Arlt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/lokku/leaflet-opencage-search">Leaflet.OpenCage.Search</a>
		</td>
		<td>
			使用 <a href="http://geocoder.opencagedata.com/">OpenCage Data 的地理编码 API</a> 的搜索插件。
		</td>
		<td>
			The <a href="https://github.com/opencagedata">OpenCage</a> team
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/consbio/Leaflet.Geonames">Leaflet.Geonames</a>
		</td>
		<td>
			由 <a href="http://www.geonames.org/">GeoNames</a> 提供支持的轻量级地理编码控件。  <a href="https://consbio.github.io/Leaflet.Geonames">Demo</a>
		</td>
		<td>
			<a href="https://github.com/brendan-ward">Brendan Ward</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/pelias/leaflet-plugin">Pelias Leaflet Plugin</a>
		</td>
		<td>
			使用 <a href="https://geocode.earth">Geocode Earth</a> 或任何由 <a href="https://github.com/pelias/api">Pelias Geocoder API</a> 提供的托管服务的地理编码控件。 <a href="https://pelias.github.io/leaflet-plugin/">Demo</a>
		</td>
		<td>
			<a href="https://github.com/louh">Lou Huang</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/tomik23/Leaflet.Autocomplete">Leaflet.Autocomplete</a>
		</td>
		<td>
			Leaflet.Autocomplete is to expand the autosugestion plugin with the ability to geocode and show data on the map in the way you think you need. The <a href="https://tomik23.github.io/Leaflet.Autocomplete/">DEMO</a> is based on the use of OpenstreetMap Nominatim to locate places by address. Accessible, with full support for ARIA attributes and keyboard interactions.
		</td>
		<td>
			<a href="https://github.com/tomik23">Grzegorz Tomicki</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/location-iq/leaflet-geocoder">Leaflet LocationIQ Geocoder</a>
		</td>
		<td>
			一个插件，增加了使用 <a href="https://locationiq.com/">LocationIQ</a> 搜索（地理编码）由 Leaflet 驱动的地图的能力。
		</td>
		<td>
			<a href="https://github.com/location-iq">LocationIQ</a>
		</td>
	</tr>
		<tr>
		<td>
			<a href="https://github.com/mmaciejkowalski/L.Highlight">L.Highlight</a>
		</td>
		<td>
			一个插件，增加了使用 <a href="https://nominatim.org/">Nominatim</a> 快速突出显示街道和地区的功能。
		</td>
		<td>
			<a href="https://github.com/mmaciejkowalski">Maciej Kowalski</a>
		</td>
	</tr>
</table>



### Plugin collections

横跨几个类别的插件集。

插件开发人员：请将未来的插件保存在单独的存储库中。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/shramov/leaflet-plugins">Plugins by Pavel Shramov</a>
		</td><td>
				一组插件：GPX、KML、TOPOJSON 图层；Bing 图层；Yandex 层（使用其 API 实现）和永久链接控制。
		</td><td>
			<a href="https://github.com/shramov">Pavel Shramov</a>, <a href="https://github.com/brunob">Bruno B</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Estimap/Spectrum4Leaflet">Spectrum4Leaflet</a>
		</td><td>
			使用带有 Leaflet 的 Spectrum Spatial Server 服务的工具。该插件支持：地图服务、瓦片服务、要素服务。它具有图层、图例和功能控件。
		</td><td>
			<a href="https://github.com/SVoyt">SVoyt</a>, <a href="https://github.com/Estimap">ESTI MAP</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://mapbbcode.org/leaflet.html">MapBBCode-related leaflet plugins</a>
		</td><td>
			七个用于各种功能的插件，独立于MapBBCode库。
			从圆形和弹出式图标到按钮、图层切换器、更好的搜索和属性。
		</td><td>
			<a href="https://github.com/zverik">Ilya Zverev</a>
		</td>
	</tr>
</table>



## 综合的

### Frameworks & build systems

将 Leaflet 集成到一个开发框架中，或为复杂的应用程序自动处理一些 javascript/CSS 工作，以简化你的开发工作。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/ghybs/leaflet-defaulticon-compatibility">leaflet-defaulticon-compatibility</a>
		</td><td>
			从 CSS 中检索所有 Leaflet 默认图标选项，特别是所有图标图像 URL，以提高与在 CSS 中修改 URL 的捆绑器和框架的兼容性。特别是对于 webpack（带有 style-、css-、file- 和 url-loader）、Rails 资产管道和 Django 管道。应解决与<a href="https://github.com/Leaflet/Leaflet/issues/4968">问题 Leaflet/Leaflet #4968</a>相关的所有用例。<a href="https://ghybs.github.io/leaflet-defaulticon-compatibility/webpack-demo.html">使用 webpack 的 demo</a>（<a href="https://ghybs.github.io/leaflet-defaulticon-compatibility/webpack-demo.html?demo=no-plugin">不使用此插件</a>）。
		</td><td>
			<a href="https://github.com/ghybs">ghybs</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/moklick/generator-leaflet">Leaflet Yeoman Generator</a>
		</td><td>
			Yeoman 生成器，用于构建基本的 Leaflet 地图应用程序。
		</td><td>
			<a href="https://github.com/moklick">Moritz Klack</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/iamtekson/leaflet-geoserver-request">leaflet-geoserver-request</a>
		</td><td>
			Basic geoserver requests in leaflet. Currently supports wms, wfs, legend, wmsImage request on the leaflet.
		<a href="https://iamtekson.github.io/leaflet-geoserver-request/examples/maps.html">Demo</a>
		</td><td>
			<a href="https://github.com/iamtekson">Iamtekson</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/PaulLeCam/react-leaflet">react-leaflet</a>
		</td><td>
			用于 Leaflet 地图的 <a href="https://facebook.github.io/react/">React</a> 组件。
		</td><td>
			<a href="http://paullecam.github.io/">Paul Le Cam</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/leaflet-extras/leaflet.css">Leaflet.CSS</a>
		</td><td>
			从 JavaScript 中添加主要的 Leaflet CSS 文件（或任何 css），去掉条件注释。
		</td><td>
			<a href="https://github.com/calvinmetcalf">Calvin Metcalf</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Norkart/Leaflet-LayerConfig">Leaflet LayerConfig</a>
		</td><td>
			提供一个 json 文件或服务响应，其中包含图层和标记的配置，以自动设置一个 Leaflet 客户端。
		</td><td>
			<a href="https://github.com/alexanno">Alexander Nossum</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.i18n">Leaflet.i18n</a>
		</td><td>
			进行国际化处理的 Leaflet 插件。
		</td><td>
			<a href="http://yohanboniface.me">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/dagjomar/Leaflet.ZoomCSS">Leaflet ZoomLevel CSS Class</a>
		</td><td>
			为地图元素添加缩放等级的 css 类，便于根据缩放级别更新样式
		</td><td>
			<a href="https://github.com/dagjomar">Dag Jomar Mersland</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/IjzerenHein/famous-map">famous-map</a>
		</td><td>
			将 Leaflet 集成到使用 <a href='http://famo.us'>famo.us</a> Web 框架制作的应用程序中。
		</td><td>
			<a href="http://www.gloey.nl">Hein Rutjes</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/Asymmetrik/ngx-leaflet">ngx-leaflet</a>
		</td><td>
			用于 <a href="https://angular.io/">Angular.io</a> 的 Leaflet 组件和扩展。
		</td><td>
			<a href="https://asymmetrik.com/">Asymmetrik, Ltd.</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/tombatossals/angular-leaflet-directive">Angular Leaflet directive</a>
		</td><td>
			在使用 <a href='http://angularjs.org/'>AngularJS</a> 网络框架制作的应用程序中集成 Leaflet。
		</td><td>
			<a href="https://github.com/tombatossals">David Rubert</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/CleverMaps/tiny-leaflet-directive">Tiny Leaflet Directive</a>
		</td><td>
			为你的 AngularJS 应用程序提供微小的 LeafletJS 地图指令。
		</td><td>
			<a href="https://github.com/mattesCZ">Martin Tesař</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/grantHarris/leaflet-popup-angular">Leaflet Popup Angular</a>
		</td><td>
			在你的 Leaflet popups 中使用 AngularJS。它扩展了内置的 L.popup.Action。
		</td><td>
			<a href="https://github.com/grantHarris">Grant Harris</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/grantHarris/leaflet-control-angular">Leaflet Control Angular</a>
		</td><td>
			在你的 Leaflet 地图中插入和使用 Angular 化的 HTML 代码，作为 Leaflet 控件。
		</td><td>
			<a href="https://github.com/grantHarris">Grant Harris</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/yagajs/leaflet-ng2">YAGA leaflet-ng2</a>
		</td><td>
			粒度集成到 Angular2/4 中。 <a href="https://leaflet-ng2.yagajs.org/latest/examples"> demo </a>
		</td><td>
			<a href="https://github.com/yagajs">YAGA Development Team</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/leaflet-extras/leaflet-map">&lt;leaflet-map&gt;</a>
		</td><td>
			将 Leaflet 集成到使用 <a href='https://www.polymer-project.org/'>Polymer &gt;= 1.0</a> Web 组件框架制作的应用程序中。
		</td><td>
			<a href="https://github.com/nhnb">Hendrik Brummermann</a>,
			<a href="https://github.com/prtksxna">Prateek Saxena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/prtksxna/leaflet-map-component">Leaflet map component</a>
		</td><td>
			将 Leaflet 集成到使用 <a href='https://www.polymer-project.org/0.5/'>Polymer 0.5</a> Web 框架制作的应用程序中。
		</td><td>
			<a href="https://github.com/prtksxna">Prateek Saxena</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://bitbucket.org/terrayazilim/leaflet.jsf">Leaflet.jsf</a>
		</td><td>
			用于 Leaflet 的综合 Java Server Faces(JSF) 组件/包装器。
		</td><td>
			<a href="http://terrayazilim.com.tr">Terra SI LLC.</a>
			<a href="https://bitbucket.org/terrayazilim">M.Çağrı Tepebaşılı</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/themrleon/JSF2Leaf">JSF2Leaf</a>
		</td><td>
			Leaflet 的 JavaServer Faces 包装器。
		</td><td>
			<a href="https://github.com/themrleon">Leonardo Ciocari</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://miguelcobain.github.io/ember-leaflet/">ember-leaflet</a>
		</td><td>
			使用 Leaflet 为 <a href="http://emberjs.com/">Ember.js</a> 提供简单和声明性的映射。
		</td><td>
			<a href="https://github.com/miguelcobain">Miguel Andrade</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/bevanhunt/meteor-leaflet">meteor-leaflet</a>
		</td><td>
			提供了一个 Meteor 包来快速建立实时的跨平台地图应用。
		</td><td>
			<a href="https://github.com/bevanhunt">Bevan Hunt</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gregallensworth/L.Control.BootstrapModal">L.Control.BootstrapModal</a>
		</td><td>
			使用地图上的控件触发一个 Bootstrap 模态框（Modal）。
		</td><td>
			<a href="https://github.com/gregallensworth">Greg Allensworth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gregallensworth/L.Control.jQueryDialog">L.Control.jQueryDialog</a>
		</td><td>
			使用地图上的控件触发一个 jQuery UI dialog/modal。
		</td><td>
			<a href="https://github.com/gregallensworth">Greg Allensworth</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/mstahv/v-leaflet">V-Leaflet</a>
		</td><td>
			将 Leaflet 作为 <a href='https://vaadin.com/home'>Vaadin</a> Java/HTML 框架的一个组件。
		</td><td>
			<a href="https://github.com/mstahv">Matti Tahvonen</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/gwidgets/gwty-leaflet">gwty-leaflet</a>
		</td><td>
			一个用于 Leaflet 的 Java/GWT JsInterop 包装器。它允许在 Java 中使用 Leaflet，就像在 javascript 脚本中一样。
		</td><td>
			<a href="https://github.com/zak905">Zakaria Amine</a>
		</td>
	</tr>
        <tr>
		<td>
			<a href="https://github.com/gherardovarando/leaflet-map-builder">Leaflet Map Builder</a>
		</td><td>
			它从一个配置对象中填充 Leaflet 地图，还可以创建缩放、图层、属性和绘制控件。 <a href="https://gherardovarando.github.io/leaflet-map-builder/"> demo </a>
		</td><td>
			<a href="https://github.com/gherardovarando">Gherardo Varando</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/KoRiGaN/Vue2Leaflet">Vue2Leaflet</a>
		</td><td>
			<a href="https://github.com/KoRiGaN/Vue2Leaflet">Vue2Leaflet</a> 是一个用于 <a href="https://vuejs.org/">Vue.js</a> 框架的JavaScript库，它封装了 Leaflet，使其能够轻松创建交互式地图。
		</td><td>
			<a href="https://github.com/KoRiGaN">Mickaël KoRiGaN</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://github.com/axyjo/leaflet-rails">leaflet-rails gem</a>
		</td><td>
			这个 gem 为您的 Rails 5 应用程序提供了 Leaflet.js 地图显示库。<a href="https://rubygems.org/gems/leaflet-rails"> RubyGems 上的 leaflet-rails</a>。
		</td><td>
			<a href="https://github.com/axyjo">Akshay Joshi</a>
		</td>
	</tr>
</table>


### 3<sup>rd</sup> party integration

以下插件将 Leaflet 集成到第三方服务或网站中。

<table class="plugins"><tr><th>Plugin</th><th>Description</th><th>Maintainer</th></tr>
	<tr>
		<td>
			<a href="https://github.com/yohanboniface/Leaflet.EditInOSM">Leaflet.EditInOSM</a>
		</td><td>
			在主要的 OSM 编辑器上添加一个带链接的控件来打开当前地图视图。
		</td><td>
			<a href="http://yohanboniface.me">Yohan Boniface</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://www.mapsmarker.com/">Maps Marker Pro</a>
		</td><td>
			一个 WordPress 插件，使用户能够通过他们的 WordPress 支持的网站固定、组织和分享他们最喜欢的地方和曲目。
		</td><td>
			<a href="http://www.harm.co.at/">Robert Harm</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://wordpress.org/plugins/leaflet-map/">WordPress Leaflet Map</a>
		</td><td>
			交互式且灵活的 shortcode，可在帖子和页面中创建多个地图，并在这些地图上添加多个标记。
		</td><td>
			<a href="https://bozdoz.com/projects/leaflet-map">Benjamin J DeLong</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://maptiks.com">Maptiks</a>
		</td>
		<td>
			网络地图分析平台，跟踪地图活动、图层加载时间、标记点击等！
		</td>
		<td>
			<a href="http://www.sparkgeo.com/">Sparkgeo</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://drupal.org/project/leaflet">Leaflet for Drupal</a>
		</td><td>
			一个 Drupal（7.x 和 8.x）模块，用于在您的 Drupal 站点中集成 Leaflet 地图。包含一个字段格式化程序来显示包含地理空间数据的字段的地图，视图集成以在地图上绘制数据，以及一个轻量级且易于使用的 API。目前被超过 10.000 个站点使用。
		</td><td>
			<a href="http://marzeelabs.org">Marzee Labs</a>, and more maintainers listed at <a href="http://drupal.org/project/leaflet">drupal.org</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://lapizistik.github.io/leaflet-easymap/">Leaflet Easymap</a>
		</td><td>
			在您的 HTML 页面中引入一张地图，而无需进行任何编程。一个数据驱动的 Javascript 模块。
		</td><td>
			<a href="https://github.com/Lapizistik">Klaus Stein</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="http://wp-mapit.phpwebdev.in">WP MapIt</a>
		</td><td>
			Open Street Map 和 Leaflet，带有自定义标记图像、描述和链接。
		</td><td>
			<a href="http://phpwebdev.in/">Chandni Patel</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://wordpress.org/plugins/map-block-leaflet/">Map Block Leaflet</a>
		</td><td>
			一个基于 Leaflet 的新 WordPress 区块编辑器的区块，它允许从一个可视化界面添加和定制地图。
		</td><td>
			<a href="https://goiblas.com/">Jesús Olazagoitia</a>
		</td>
	</tr>
	<tr>
		<td>
			<a href="https://community.mybb.com/mods.php?action=view&pid=1238">ABP Usermap MyBB</a>
		</td><td>
		    一个用于 <a href="https://mybb.com/">MyBB</a> 的插件，基于 Open Street Map 和 Leaflet 创建用户地图，并可自定义弹出窗口和标记。
		</td><td>
			<a href="https://gitlab.com/AnoBug">CrazyCat</a>
		</td>
	</tr>
  <tr>
		<td>
      Leaflet Extensions for <a href="https://www.joomla.org/">Joomla! (3.x)</a>
		</td><td>
			<ul>
        <li>
          <strong>Agosm: </strong><br />
          Joomla 模块不仅用于在 OpenStreetMap 地图上显示标记。
          <a href="https://github.com/astridx/pkg_agosms">Gibhub</a><br />
          <a href="https://extensions.joomla.org/extensions/extension/maps-a-weather/maps-a-locations/agosm/">Joomla扩展目录</a><br />
        </li>
        <li>
            <strong>Aggpxtrack: </strong><br />
            Joomla自定义字段用于在地图上发送GPX轨迹 - 你可以选择OpenStreetMap或GoogleMaps。有很多选项。比如说。其中一个选项是高程剖面图。
            <a href="https://github.com/astridx/pkg_aggpxtrack">Gibhub</a><br />
            <a href="https://extensions.joomla.org/extensions/extension/maps-a-weather/maps-a-locations/aggpxtrack/">Joomla扩展目录</a><br />
        </li>
        <li>
            <strong>Agosmmapwithmarker: </strong><br />
            自定义字段，用于显示一个带有标记的地图，在边缘端--总是正确的内容卡。你可以在后台输入地址。
            <a href="https://github.com/astridx/plg_fields_agosmmapwithmarker">Gibhub</a><br />
            <a href="https://extensions.joomla.org/extensions/extension/maps-a-weather/maps-a-locations/agosmmapwithmarker/">Joomla Extension Directory</a><br />
        </li>
    </ul>
		</td><td>
			<a href="https://github.com/astridx">Astrid Günther</a>
    </td>
  </tr>
  <tr>
	<td>
		<a href="https://github.com/mwasil/Leaflet.Facebook/">Leaflet.Facebook</a>
	</td><td>
		用于添加 Facebook 点赞按钮作为控件的简单插件。
	  </td><td>
		<a href="https://marcinwasilewski.eu/u">Marcin Wasilewski</a>
	</td>
  </tr>
  <tr>
	<td>
		<a href="https://github.com/alexboia/WP-Trip-Summary/">WP-Trip-Summary</a>
	</td><td>
		一个 WordPress 旅行总结插件，可帮助旅游博主管理和显示有关他们乘坐火车、骑自行车或徒步旅行的结构化信息。
	  </td><td>
		<a href="https://wordpress.org/plugins/wp-trip-summary/">Alexandru Boia</a>
	</td>
  </tr>
  <tr>
	<td>
		<a href="https://wordpress.org/plugins/open-user-map/">Open User Map – Users can add locations from the frontend</a>
	</td><td>
		WordPress plugin to let your visitors add locations directly from the frontend - without registration. They drop a marker on the map and provide some location details. After submit the location proposal will be “pending” and wait for your review approval to get published.
	  </td><td>
		<a href="https://www.open-user-map.com/">100plugins</a>
	</td>
  </tr>
</table>



## Develop your own

Leaflet 保持简单。如果你能想到一个并非所有 Leaflet 用户都需要的功能，并且你能以一种可重复使用的方式编写 JavaScript 代码，你就已经有了一个 Leaflet 插件。

对于如何创建自己的插件没有硬性要求，但我们鼓励所有的开发者阅读[插件指南](https://github.com/Leaflet/Leaflet/blob/master/PLUGIN-GUIDE.md)中的建议。

一旦您的插件准备就绪，您就可以将其提交到此列表：只需将添加到 [/docs/plugins.md](https://github.com/Leaflet/Leaflet/blob/master/docs/plugins.md) 的 PR 发送到我们的 GitHub 存储库。
