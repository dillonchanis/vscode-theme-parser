<template>
  <div id="app">
    <div class='container'>
      <AppHeader />
      <AppForm @onClear="json = ''"
               @onSubmit="onSubmit" />
      <AppPaletteContainer :json="json" />
    </div>
  </div>
</template>

<script>
import AppHeader from './components/Header'
import AppForm from './components/Form/FormContainer'
import AppPaletteContainer from './components/Palette/PaletteContainer'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppForm,
    AppPaletteContainer
  },
  data: () => ({
    json: null
  }),
  methods: {
    onSubmit(json) {
      this.json = JSON.parse(json)
    }
  }
}
</script>

<style>
::selection {
  background: rgba(232, 48, 140, 0.15);
}

#app {
  font-family: 'Lora', serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  margin-top: 35px;
  color: #3c424f;
}

.container {
  width: 100%;
  padding: 15px;
  margin: 0 auto;
}

@media screen and (min-width: 1080px) {
  .container {
    width: 1080px;
  }
}
</style>
