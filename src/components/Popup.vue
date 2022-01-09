<template>
    <section @animationend="animationend" @click.self="closePop" :class="{popupShowAni: isShow, popupHideAni: !isShow}">
        <img :src="src" alt="">
    </section>
</template>

<script>
export default {
    name: 'Popup',
    data() {
        return {
            isShow: false
        }
    },
    props: ['src'],
    mounted() {
        this.isShow = true
    },
    methods: {
        closePop() {
            this.isShow = false
        },
        animationend() {
            !this.isShow && this.$parent.setPopup(false)
        }
    }
}
</script>

<style scoped>
section {
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, 0.8);
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 10;
}

.popupShowAni {
    animation: popupShowAni 0.2s ease forwards;
}
@keyframes popupShowAni {
    0% { opacity: 0; transform: scale(0); }
    100% { opacity: 1; transform: scale(1); }
}
.popupHideAni {
    animation: popupHideAni 0.2s ease forwards;
}
@keyframes popupHideAni {
    0% { opacity: 1; transform: scale(1); }
    100% { opacity: 0; transform: scale(0); }
}
</style>