<template>
  <div id="app">
    <Header :baseUrl="baseUrl" :type="type" />
    <Main :baseUrl="baseUrl" :type="type" />
    <Popup v-show="isPopup" :isPopup="isPopup" :src="src" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Popup from './components/Popup.vue'

export default {
  name: 'App',
  data() {
    return {
      baseUrl: 'http://morefun-active.oss-cn-beijing.aliyuncs.com/bao_daily/barry-film',
      src: '',
      type: 'photo',
      isPopup: false
    }
  },
  mounted() {
  },
  methods: {
    /**
     * 设置当前显示图片或视频
     */
    setType(type) {
      this.type = type
    },
    /**
     * 设置弹窗显示隐藏
     */
    setPopup(state, src='') {
      this.src = src
      this.isPopup = state
    }
  },
  components: { Header, Main, Popup }
}
</script>

<style>
* { margin: 0; padding: 0; box-sizing: border-box; }
ul, ol, li { list-style: none; }
img, video { max-width: 100%; }

.icon {
    width: 1em; height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}

#app {
  width: 100vw;
  height: 100vh;
  background: url("//morefun-active.oss-cn-beijing.aliyuncs.com/bao_daily/barry-film/photos/93.jpg") no-repeat center top;
  background-size: 100% 100%;
  overflow: hidden;
}
</style>
