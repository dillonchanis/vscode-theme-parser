<template>
  <div class="palette-list-container">
    <template v-if="json">
      <AppPaletteList :palettes="colorPalettes" />
    </template>
  </div>
</template>

<script>
import AppPaletteList from "./PaletteList";
import { UUIDGenerator, orderBy } from "../../utils";

export default {
  name: "AppPaletteContainer",
  components: {
    AppPaletteList
  },
  props: {
    json: {
      type: [Object, String],
      default: null
    }
  },
  computed: {
    colors() {
      return this.json.colors;
    },
    colorAmountMap() {
      return Object.keys(this.colors)
        .map(property => this.colors[property])
        .reduce((prev, curr) => {
          prev[curr] = (prev[curr] || 0) + 1;
          return prev;
        }, {});
    },
    unOrderedColorPalettes() {
      return Object.keys(this.colorAmountMap)
        .map(color => {
          return {
            id: UUIDGenerator(),
            amount: this.colorAmountMap[color],
            color
          };
        })
        .filter(palette => palette.color !== "null");
    },
    colorPalettes() {
      return orderBy(this.unOrderedColorPalettes, ["amount"], ["desc"]);
    }
  }
};
</script>

<style scoped>
.palette-list-container {
  margin-top: 30px;
}
</style>
