<template>
    <main>

        <!-- 图片 -->
        <section v-show="type === 'photo'" @click="showBigImg" class="photo">
            <div>
                <img v-for="(item, index) in imgList" :key="index" :data-value="item.img" :src="item.img" alt="">
            </div>
        </section>

        <!-- 视频 -->
        <section v-show="type === 'video'" @touchstart="touchstart" @touchend="touchend" :style="styleObj" class="video">
            <div v-for="(item, index) in videoList" :key="index">
                <video :ref="`video${index}`" controls preload="metadata" loop="true">
                    <source :src="item.video" type="video/mp4">
                    Sorry, your browser doesn't support embedded videos.
                </video>
            </div>
        </section>

    </main>
</template>

<script>
export default {
    name: 'Main',
    data() {
        return {
            lastY: 0,
            currentVideo: 0
        }
    },
    props: ['type', 'imgList', 'videoList'],
    computed: {
        styleObj() {
            return { transform: `translateY(calc(-${this.currentVideo} * 100% / 10))` }
        }
    },
    methods: {
        showBigImg(e) {
            const { value } = e.target.dataset
            this.$parent.setPopup(true, value)
        },
        touchstart(e) {
            const { clientY } = e.changedTouches[0]
            this.lastY = clientY
        },
        touchend(e) {
            const { clientY } = e.changedTouches[0]
            if (clientY < this.lastY) {     // 下滑
                if (this.currentVideo >= this.videoList.length-1) return
                this.currentVideo += 1
            }
            if (clientY > this.lastY) {     // 上滑
                if (this.currentVideo <= 0) return
                this.currentVideo -= 1
            }
            this.stopPlayAllVideo()    
            this.$refs[`video${this.currentVideo}`][0].play()
        },
        stopPlayAllVideo() {
            for (let i = 0; i < this.videoList.length; i ++) {
                this.$refs[`video${i}`][0].pause()
                this.$refs[`video${i}`][0].currentTime = 0
            }
        }
    },
    watch: {
        type(value) {
            if (value === 'photo') this.stopPlayAllVideo()
            if (value === 'video') this.$refs[`video${this.currentVideo}`][0].play()
        }
    }
}
</script>

<style scoped>
main {
    height: calc(100vh - 90px - 100px);
    overflow: hidden;
    margin-top: 20px;
}

/* 图片 */
.photo {
    height: 100%;
    overflow-y: auto;
}
.photo > div {
    column-count: 2;
    column-gap: 6px;
}
.photo > div > img {
    display: block;
    margin-top: 6px;
}

/* 视频 */
.video {
    height: calc(100% * 10);
    transition: all 0.5s;
}
.video > div {
    height: calc(100% / 10);
    background-color: #111;
    overflow: hidden;
    display: flex;
    align-items: center;
}
.video > div > video {
    width: 100%;
}
</style>