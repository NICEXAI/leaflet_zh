---
layout: tutorial_frame
title: WMS example
---
<script type='text/javascript'>

	const map = L.map('map', {
		center: [-17, -67],
		zoom: 3
	});

	const basemaps = {
		Topography: L.tileLayer.wms('http://ows.mundialis.de/services/service?', {
			layers: 'TOPO-WMS'
		}),

		Places: L.tileLayer.wms('http://ows.mundialis.de/services/service?', {
			layers: 'OSM-Overlay-WMS'
		}),

		'Topography, then places': L.tileLayer.wms('http://ows.mundialis.de/services/service?', {
			layers: 'TOPO-WMS,OSM-Overlay-WMS'
		}),

		'Places, then topography': L.tileLayer.wms('http://ows.mundialis.de/services/service?', {
			layers: 'OSM-Overlay-WMS,TOPO-WMS'
		})
	};

	const layerControl = L.control.layers(basemaps, {}, {collapsed: false}).addTo(map);

	basemaps.Topography.addTo(map);

</script>
