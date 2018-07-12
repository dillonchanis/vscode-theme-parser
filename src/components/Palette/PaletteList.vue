<template>
  <transition name="slide">
    <ul class="palette-list"
        v-if="palettes.length">
      <AppPaletteListItem v-for="(palette, index) in palettes"
                          :key="palette.id"
                          :data-index="index"
                          :palette="palette" />
    </ul>
  </transition>
</template>

<script>
import AppPaletteListItem from "./PaletteListItem";

export default {
  name: "AppPaletteList",
  components: {
    AppPaletteListItem
  },
  props: {
    palettes: {
      type: Array
    }
  }
};
</script>

<style scoped>
.palette-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  list-style: none;
  margin: 0;
  padding: 0;
}

.slide-enter-active {
  animation: slide-in 500ms ease-out;
}

.slide-leave-active {
  animation: slide-out 500ms ease-out;
}

@keyframes slide-in {
  from {
    transform: translateX(-30px);
    opacity: 0;
  }
  to {
    transform: translateX(0px);
    opacity: 1;
  }
}

@keyframes slide-out {
  from {
    transform: traslateX(0px);
    opacity: 1;
  }
  to {
    transform: translateX(-30px);
    opacity: 0;
  }
}
</style>
