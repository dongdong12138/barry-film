<template>
    <main>

        <!-- 图片 -->
        <section class="photo">
            <img v-for="(item, index) in imgList" :key="index" :src="item.img" alt="">
        </section>

    </main>
</template>

<script>
export default {
    name: 'Main',
    data() {
        return {
            imgList: []
        }
    },
    created() {
        for (let i = 1; i <= 100; i ++) {
            this.imgList.push({ img: require(`../assets/photos/${i}.jpg`) })
        }
    }
}
</script>

<style scoped>
main {
    /* border: 2px solid green; */
    height: calc(100vh - 90px - 100px);
    overflow: hidden auto;
    margin-top: 20px;
}

/* 图片 */
.photo {
    column-count: 2;
    column-gap: 6px;
}
.photo > img {
    display: block;
    margin-top: 6px;
}
</style>