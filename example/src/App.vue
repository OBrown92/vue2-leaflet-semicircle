<template>
  <div id="app">
    <l-map :zoom="10" :center="mapCenter">
      <l-tile-layer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></l-tile-layer>
      <v-semicircle
        v-for="(item, index) in semiCircle"
        :key="'semicircle-' + index"
        :latLng="[item.location.lat, item.location.lng]"
        :options="item.options"
      ></v-semicircle>
    </l-map>
  </div>
</template>

<script>
import Vue from "vue";
import { latLng } from "leaflet";
import { LMap, LTileLayer } from "vue2-leaflet";

// import Vue2LeafletSemicircle from 'vue2-leaflet-semicircle' // this is for production
import Vue2LeafletSemicircle from "./Vue2LeafletSemicircle"; // this is used in development to work on the source

Vue.component("v-semicircle", Vue2LeafletSemicircle);

export default {
  name: "app",
  components: {
    LMap,
    LTileLayer
  },
  data() {
    return {
      mapCenter: [52.457783, 7.1825],
      semiCircle: [
        {
          location: latLng(52.457783, 7.1825),
          options: {
            startAngle: 45,
            stopAngle: 90,
            radius: 2000,
          },
        }, {
          location: latLng(52.457783, 7.1825),
          options: {
            startAngle: 135,
            stopAngle: 180,
            radius: 3000,
          },
        }, {
          location: latLng(52.457783, 7.1825),
          options: {
            startAngle: 225,
            stopAngle: 270,
            radius: 4000,
          },
        }, {
          location: latLng(52.457783, 7.1825),
          options: {
            startAngle: 315,
            stopAngle: 360,
            radius: 5000,
          },
        },
      ],
    };
  },
};
</script>

<style>
/* @import "~leaflet/dist/leaflet.css"; */

#app {
  width: 1024px;
  height: 768px;
  margin-top: 60px;
}
</style>
