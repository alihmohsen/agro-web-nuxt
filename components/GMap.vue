<template>
  <DxVectorMap
    id="vector-map"
    :bounds="bounds"
    :zoomFactor="1"
    :zoomingEnabled="false"
    :wheelEnabled="false"
    :disabled="false"
    :panningEnabled="false"
  >
    <DxLayer
      :data-source="worldData"
      :customize="customizeLayer"
      :color-groups="colorGroups"
      color-grouping-field="population"
      name="areas"
      palette="Pastel"
    />

    <DxLegend
      :customize-text="customizeText"
    >
      <DxSource
        layer="areas"
        grouping="color"
      />
    </DxLegend>
  </DxVectorMap>
</template>
<script>

import * as mapsData from 'devextreme/dist/js/vectormap-data/world.js';

import {
  DxVectorMap,
  DxLayer,
  DxLegend,
  DxSource,
} from 'devextreme-vue/vector-map';

import { countries,populations } from '../data.js';

export default {
  components: {
    DxVectorMap,
    DxLayer,
    DxLegend,
    DxSource,
  },
  data() {
    return {
      worldData: mapsData.world,
      bounds: [-180, 85, 180, -60],
      colorGroups: [0, 0.5, 0.8],
    };
  },
  methods: {
    customizeLayer(elements) {
      elements.forEach((element) => {
        const country = countries[element.attribute('name')];
        element.attribute('population', populations[element.attribute('name')]);
        if (country) {
          element.applySettings({
            color: country.color,
          });
        }
      });
    },

    customizeText(itemInfo) {
      let text;
      if (itemInfo.index === 0) {
        text = 'Export Countries';
      } else if (itemInfo.index === 1) {
        text = 'Import Countries';
      }
      return text;
    },
  },
};
</script>
<style>
#vector-map {
  height: 600px;
}

@media (max-width:600px){
  #vector-map {
    height: 300px;
  }
}

.dxm-control-bar{
  display: none;
}

.dxm-background{
  fill: #404a3d;
  x:0;
  y:0;
  stroke: none;
  stroke-width: 0;
}
</style>
