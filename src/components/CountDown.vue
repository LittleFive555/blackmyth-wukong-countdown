<script>
export default {
    props: ["endTime"],
    setup() {
    },
    data() {
        return {
            remainTime: 0,
            timer: null
        }
    },
    computed: {
        remainTimeStr() {
            let day = Math.floor(this.remainTime / 24 / 60 / 60 / 1000)
            let hour = Math.floor(this.remainTime / 60 / 60 / 1000 % 24)
            let minutes = Math.floor(this.remainTime / 60 / 1000 % 60)
            let seconds = Math.floor(this.remainTime / 1000 % 60)
            return `${day}天${hour}小时${minutes}分${seconds}秒`
        }
    },
    methods: {
        updateRemainTime() {
            let nowTime = new Date()
            let targetTime = new Date(this.endTime)
            if (targetTime > nowTime) {
                this.remainTime = targetTime - nowTime
            }
            else {
                this.remainTime = 0
            }
        }
    },
    mounted() {
        this.updateRemainTime()
        this.timer = setInterval(() => { this.updateRemainTime() },1000)
    },
    unmounted() {
        clearInterval(this.timer)
    }
}
</script>

<template>
    <p>距離黑神話悟空開啓：</p>
    <p>{{ remainTimeStr }}</p>
</template>