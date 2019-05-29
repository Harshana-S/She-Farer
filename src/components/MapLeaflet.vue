<template>
<div>
    <l-map id="map"></l-map>
</div>
</template>
<script>
import {LMap, LTileLayer, LMarker } from 'vue2-leaflet';
export default {
    name: "MapLeaflet",
    components:{
    LMap,
    LTileLayer,
    LMarker 
    }
}
</script>
<style>
@import "~leaflet/dist/leaflet.css";
#map {
  width: 100%;
  height: 500px;
}
</style>
