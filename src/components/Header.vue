<template functional>
  <header class='header'>
    <h1 class='title'>VSCode Theme Parser</h1>
    <p class='tagline'>
      <span class='tagline__text'>Generate color palettes of your favorite VSCode themes. Paste the theme's JSON into the textarea to begin generating the theme's palette.</span>
      <span aria-hidden="true" class='flare'></span>
    </p>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  functional: true
};
</script>

<style scoped>
.title {
  font-family: "Open Sans", sans-serif;
  font-size: 42px;
  margin: 0;
  line-height: 54px;
}

.tagline {
  width: 90%;
  position: relative;
  font-size: 18px;
  line-height: 32px;
}

.tagline__text {
  z-index: 10;
}

.flare {
  display: block;
  position: absolute;
  top: 15px;
  left: 0;
  background-color: #e8308c;
  height: 12px;
  width: 80px;
  opacity: 0.2;
  z-index: 1;
}

@media screen and (min-width: 1080px) {
  .title {
    font-size: 52px;
  }

  .tagline {
    font-size: 22px;
    width: 55%;
  }

  .flare {
    width: 98px;
  }
}
</style>
