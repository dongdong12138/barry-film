<template>
    <div class="loading">
        <div class="box">
            <div class="loader-17"></div>
            <div class="percent">{{percent}}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: "Loading",
    data() {
        return {
            loadedCount: 0,
            percent: '0%'
        }
    },
    props: ["imgList"],
    mounted() {
        this.imgList.forEach((value) => {
            const image = new Image();
            image.src = value.img;
            image.onload = () => {
                this.loadedCount += 1;
                const percentNum = Math.floor(this.loadedCount / this.imgList.length * 100)
                this.percent = `${percentNum}%`
                if (percentNum >= 100) {
                    setTimeout(() => {
                        this.$parent.setLoading(false)
                    }, 500)
                }
            };
        });
    },
};
</script>

<style scoped>
.loading {
    width: 100%;
    height: 100vh;
    background: #323943;
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    left: 0;
    top: 0;
    z-index: 10;
}
.box {
    display: inline-block;
    width: 200px;
    height: 200px;
    /* border: 1px solid currentcolor; */
    border-radius: 3px;
    font-size: 30px;
    color: rgba(200, 200, 200, 0.5);
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    transition: .3s color, .3s border;
}
[class*="loader-"] {
    display: inline-block;
    width: 1em;
    height: 1em;
    color: inherit;
    vertical-align: middle;
    pointer-events: none;
}
.loader-17 {
    position: relative;
    background-color: currentcolor;
    border-radius: 50%;
    margin-bottom: 50px;
}
.loader-17:after,
.loader-17:before {
    content: "";
    position: absolute;
    width: .25em;
    height: .25em;
    border-radius: 50%;
    opacity: .8;
}
.loader-17:after {
    left: -.5em;
    top: -.25em;
    background-color: currentcolor;
    -webkit-transform-origin: .75em 1em;
    transform-origin: .75em 1em;
    -webkit-animation: loader-17 1s linear infinite;
    animation: loader-17 1s linear infinite;
    opacity: .6;
}
.loader-17:before {
    left: -1.25em;
    top: -.75em;
    background-color: currentcolor;
    -webkit-transform-origin: 1.5em 1em;
    transform-origin: 1.5em 1em;
    -webkit-animation: loader-17 2s linear infinite;
    animation: loader-17 2s linear infinite;
}
@-webkit-keyframes loader-17 {
    0% {
        -webkit-transform: rotateZ(0deg) translate3d(0, 0, 0);
        transform: rotateZ(0deg) translate3d(0, 0, 0);
    }
    100% {
        -webkit-transform: rotateZ(360deg) translate3d(0, 0, 0);
        transform: rotateZ(360deg) translate3d(0, 0, 0);
    }
}
@keyframes loader-17 {
    0% {
        -webkit-transform: rotateZ(0deg) translate3d(0, 0, 0);
        transform: rotateZ(0deg) translate3d(0, 0, 0);
    }
    100% {
        -webkit-transform: rotateZ(360deg) translate3d(0, 0, 0);
        transform: rotateZ(360deg) translate3d(0, 0, 0);
    }
}
</style>