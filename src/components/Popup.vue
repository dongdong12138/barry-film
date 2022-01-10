<template>
    <section @animationend="animationend" @click="closePop" :class="{ popupShowAni: !isClose, popupHideAni: isClose }">
        <img :src="src" alt="" />
    </section>
</template>

<script>
export default {
    name: "Popup",
    data() {
        return {
            isClose: false,
        };
    },
    props: ["src", "isPopup"],
    methods: {
        closePop() {
            this.isClose = true;
        },
        animationend() {
            this.isClose && this.$parent.setPopup(false);
            this.isClose = false;
        },
    },
};
</script>

<style scoped>
section {
    width: 100%;
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
    0% {
        opacity: 0;
        transform: scale(0);
    }
    100% {
        opacity: 1;
        transform: scale(1);
    }
}
.popupHideAni {
    animation: popupHideAni 0.2s ease forwards;
}
@keyframes popupHideAni {
    0% {
        opacity: 1;
        transform: scale(1);
    }
    100% {
        opacity: 0;
        transform: scale(0);
    }
}
</style>