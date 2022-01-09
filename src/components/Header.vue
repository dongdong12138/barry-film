<template>
    <header>

        <!-- 头像 -->
        <div class="avatar">
           <img src="../assets/avatar.jpg" alt="avatar">
        </div>

        <!-- 导航栏 -->
        <ul class="nav">
            <li>照片</li>
            <li>视频</li>
        </ul>

        <!-- 音乐开关 -->
        <svg @click="toggleMusic" class="icon" aria-hidden="true">
            <use v-if="playMusic" xlink:href="#icon-musicfill"></use>
            <use v-else xlink:href="#icon-musicforbidfill"></use>
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
    methods: {
        toggleMusic() {
            this.playMusic = !this.playMusic
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
    border: 1px solid pink;
    color: #ddd;
    padding: 10px 15px;
}
.nav > li.active {
    color: #fff;
}

/* 音乐开关 */
.icon {
    font-size: 40px;
    position: absolute;
    right: 10px;
}
</style>