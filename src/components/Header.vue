<template>
    <header>

        <!-- 头像 -->
        <div class="avatar">
           <img src="../assets/avatar.jpg" alt="avatar">
        </div>

        <!-- 导航栏 -->
        <ul @click="selectType" class="nav">
            <li data-type="photo" :class="{active: type === 'photo'}">照片</li>
            <li data-type="video" :class="{active: type === 'video'}">视频</li>
        </ul>

        <!-- 音乐开关 -->
        <svg @click="toggleMusic" v-if="type === 'photo'" class="icon" aria-hidden="true">
            <use v-if="playMusic" xlink:href="#icon-musicfill"></use>
            <use v-else xlink:href="#icon-musicforbidfill"></use>
        </svg>
        <audio v-if="type === 'photo'" ref="audio" :src="`${baseUrl}/music/岑宁儿 - 追光者.mp3`">
            Your browser does not support the <code>audio</code> element.
        </audio>

        <svg v-if="type === 'video'" class="icon" aria-hidden="true">
            <use xlink:href="#icon-happy"></use>
        </svg>

    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {
            playMusic: false
        }
    },
    props: ['baseUrl', 'type'],
    methods: {
        selectType(e) {
            const { type } = e.target.dataset
            this.$parent.setType(type)
        },
        toggleMusic() {
            this.playMusic = !this.playMusic
            if (this.playMusic) {
                this.$refs.audio.play()
            } else {
                this.$refs.audio.pause()
            }
        }
    }
}
</script>

<style scoped>
header {
    font-size: 20px;
    display: flex;
    align-items: center;
    position: relative;
    margin-top: 10px;
}

/* 头像 */
.avatar {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    overflow: hidden;
    margin-left: 20px;
}
.avatar > img {
    width: 100%;
}

/* 导航栏 */
.nav {
    display: flex;
    align-items: center;
    margin-left: 20px;
}
.nav > li {
    color: #ccc;
    padding: 10px 15px;
}
.nav > li.active {
    color: #fff;
    border-bottom: 2px solid #000;
}

/* 音乐开关 */
.icon {
    font-size: 40px;
    position: absolute;
    right: 10px;
}
</style>