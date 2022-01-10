<template>
    <div class="Letters">
        {{letter}}
    </div>    
</template>

<script>
export default {
    name: 'Letters',
    data() {
        return {
            letter: '',
            letterArr: [
                '不要因为没有掌声就放弃梦想。',
                '梦里相见却相顾无言。',
                '记得在这杂乱的生活里，每天带点笑意。',
                '不远万里，我想见你。',
                '思念无果，大雨滂沱。',
                '一切都会变好的，超好，爆好，无敌好。',
                '一个人，一本书，一杯茶，一帘梦。',
                '你未必万丈光芒，但你温暖有光。',
                '想和有趣的人浪费时间，比如和你。',
                '要及时清醒也要事事如意。'
            ]
        }
    },
    mounted() {
        const timer = setInterval(() => {
            const random = parseInt(Math.random() * (this.letterArr.length+1))
            this.letter = this.letterArr[random]
        }, 5000)
    }
}
</script>

<style scoped>
.Letters {
    padding: 10px;
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    background-image: linear-gradient(to right, orange, purple);
    background-clip: text;
    color: transparent;
    margin-top: 10px;
}
</style>