<template>
  <div id="app">
    <Header :baseUrl="baseUrl" :type="type" />
    <Main :imgList="imgList" :videoList="videoList" :type="type" />
    <Letters />
    <Popup v-show="isPopup" :isPopup="isPopup" :src="src" />
    <Loading v-if="isLoading" :imgList="imgList" />
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import Popup from './components/Popup.vue'
import Loading from './components/Loading.vue'
import Letters from './components/Letters.vue'

export default {
  name: 'App',
  data() {
    return {
      baseUrl: 'http://morefun-active.oss-cn-beijing.aliyuncs.com/bao_daily/barry-film',
      src: '',
      type: 'photo',
      imgList: [],
      videoList: [],
      isPopup: false,
      isLoading: true,
    }
  },
  created() {
      for (let i = 1; i <= 100; i ++) {
        // this.imgList.push({ img: require(`${this.baseUrl}/photos/${i}.jpg`) })
        this.imgList.push({ img: `${this.baseUrl}/photos/${i}.jpg` })
      }
      for (let i = 1; i <= 10; i ++) {
        // this.videoList.push({ video: require(`${this.baseUrl}/videos/${i}.mp4`) })
        this.videoList.push({ video: `${this.baseUrl}/videos/${i}.mp4` })
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
    },
    /**
     * 设置Loading显示隐藏
     */
    setLoading(state) {
      this.isLoading = state
    }
  },
  components: { Header, Main, Popup, Loading, Letters }
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
  font-family: -apple-system, "Noto Sans", "Helvetica Neue", Helvetica, "Nimbus Sans L", Arial, "Liberation Sans", "PingFang SC", "Hiragino Sans GB", "Noto Sans CJK SC", "Source Han Sans SC", "Source Han Sans CN", "Microsoft YaHei", "Wenquanyi Micro Hei", "WenQuanYi Zen Hei", "ST Heiti", SimHei, "WenQuanYi Zen Hei Sharp", sans-serif;
  overflow: hidden;
}
@media screen and (min-width: 500px) {
  #app {
    width: 500px;
    margin: 0 auto;
  }
}
</style>
