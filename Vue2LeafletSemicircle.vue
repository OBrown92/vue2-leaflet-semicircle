<template>
  <div>
    <slot v-if="ready"></slot>
  </div>
</template>

<script>
import { DomEvent, semiCircle } from "leaflet";
import { findRealParent, propsBinder } from "vue2-leaflet";
import "leaflet-semicircle";

const props = {
  latLng: {
    type: Array,
  },
  options: {
    type: Object,
  },
  visible: {
    type: Boolean,
    custom: true,
    default: true,
  },
};

export default {
  props: props,
  data() {
    return {
      ready: false,
    };
  },
  mounted() {
    let options = {};

    options.radius = this.options.radius || 500;
    options.startAngle = this.options.startAngle || 45;
    options.stopAngle = this.options.stopAngle || 135;

    this.mapObject = semiCircle(this.latLng, options);
    DomEvent.on(this.mapObject, this.$listeners);
    propsBinder(this, this.mapObject, props);
    this.ready = true;
    this.parentContainer = findRealParent(this.$parent);
    this.parentContainer.addLayer(this, !this.visible);
  },
  beforeDestroy() {
    this.parentContainer.removeLayer(this);
  },
  methods: {
    setVisible(newVal, oldVal) {
      if (newVal === oldVal) return;
      if (this.mapObject) {
        if (newVal) {
          this.mapObject.addTo(this.parent);
        } else {
          this.parent.removeLayer(this.mapObject);
        }
      }
    },
  },
};
</script>