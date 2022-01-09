<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import Header from './components/Header.vue'

export default {
  name: 'App',
  data() {
    return {
    }
  },
  components: { Header }
}
</script>

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
ul, ol, li { list-style: none; }

.icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}

#app {
  width: 100vw;
  height: 100vh;
  background: url("./assets/photos/IMG_9546.jpg") no-repeat center top;
  background-size: 100% 100%;
  overflow: hidden;
  border: 1px solid red;
}
</style>
