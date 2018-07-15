<template>
  <li class="palette"
      @click="copyToClipboard">
    <div class="swatch"
         :style="{ backgroundColor: palette.color }"></div>
    <div class="swatch__info">
      {{ palette.color }} ({{ palette.amount }})
    </div>
  </li>
</template>

<script>
export default {
  name: 'AppPalette',
  props: {
    palette: {
      type: Object
    }
  },
  methods: {
    copyToClipboard() {
      const temp = document.createElement('input')
      temp.setAttribute('value', this.palette.color)
      document.body.appendChild(temp)
      temp.select()
      document.execCommand('copy')
      document.body.removeChild(temp)
    }
  }
}
</script>

<style scoped>
.palette {
  width: 100%;
  margin-bottom: 2em;
  border-radius: 4px;
  box-shadow: 0 5px 15px 0 rgba(37, 44, 97, 0.15),
    0 2px 4px 0 rgba(93, 100, 148, 0.2);
}

.swatch {
  width: 100%;
  height: 100px;
  border-top-left-radius: 4px;
  border-top-right-radius: 4px;
}

.swatch__info {
  font-size: 18px;
  padding: 10px;
  text-align: center;
}

@media screen and (min-width: 530px) {
  .palette {
    width: 250px;
  }

  .swatch {
    height: 215px;
  }
}
</style>
