<template>
    <header>
        <div class="avatar">
            <img src="../assets/avatar.jpg" alt="头像">
        </div>
        <ul class="nav">
            <li @click="toggleType" data-type="photo">照片</li>
            <li @click="toggleType" data-type="video">视频</li>
        </ul>
    </header>
</template>

<script>
export default {
    name: 'Header',
    data() {
        return {

        }
    },
    methods: {
        toggleType(e) {
            const { type } = e.target.dataset
            console.log(type)
            this.$rooter.bus.$emit('toggle', '111')
        }
    }
}
</script>

<style scoped>
header {
    border: 1px solid red;
    display: flex;
}

.avatar {
    width: 80px;
    height: 80px;
    border-radius: 50%;
    overflow: hidden;
    margin-left: 50px;
}
.avatar > img {
    width: 100px;
    margin: -16px 0 0 -6px;
}

.nav {
    display: flex;
    margin-left: 40px;
}
.nav > li {
    width: 100px;
    background-color: #ccc;
    font-size: 20px;
    cursor: pointer;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 10px;
}
.nav > li:hover {
    background-color: #aaa;
}
</style>