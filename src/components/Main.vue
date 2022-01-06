<template>
    <main>
        <section class="photo">
            照片
        </section>
        <section class="video">
            视频
        </section>
    </main>
</template>

<script>
export default {
    name: 'Main',
    data() {
        return {

        }
    },
    mounted() {
        this.$rooter.bus.$on('toggle', (value) => {
            console.log(value)
        })
    }
}
</script>

<style scoped>
main {
    border: 1px solid red;
}
section.photo {
    border: 1px solid green;
    height: 200px;
}
section.video {
    border: 1px solid green;
    height: 200px;
}
</style>