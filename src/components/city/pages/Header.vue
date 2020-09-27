<template>
    <div class="header">
        <div class="header-left" @click="toHome">
            <span class="iconfont">&#xe658;</span>
        </div>
        <div class="header-title">
            城市选择
        </div>
    </div>
</template>

<script>
export default {
    methods: {
        toHome() {
            this.$router.push('/')
        }
    }
}
</script>

<style scoped lang='stylus'>
@import '~css/var.styl'

.header {
    width: 100%;
    line-height: .88rem;
    background: $bgColor;
    color: $textColor;
    font-size: .32rem;
}
.header-left{
    width: .4rem;
    padding: 0 .2rem;
    text-align: center;
    font-weight: bold;
    position absolute;
}
.header-title {
    text-align: center;
}
</style>