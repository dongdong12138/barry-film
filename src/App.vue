<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Vue from 'vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'

export default {
  name: 'App',
  data() {
    return {
      bus: new Vue()
    }
  },
  components: { Header, Main }
}
</script>

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
ul, ol, li { list-style: none; }

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 1000px;
  margin: 0 auto;
}
</style>
