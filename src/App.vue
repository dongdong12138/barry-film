<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  data() {
    return {
    }
  },
  components: { Header, Main }
}
</script>

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
ul, ol, li { list-style: none; }
img { max-width: 100%; }

.icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}

#app {
  width: 100vw;
  height: 100vh;
  background: url("./assets/photos/93.jpg") no-repeat center top;
  background-size: 100% 100%;
  overflow: hidden;
  border: 1px solid red;
}
</style>
