<template>
    <div class="header">
        <div class="header-return"
        v-show="showHeader">
            <span class="border-return"></span>
            <span class="iconfont return" @click="toHome">&#xe658;</span>
        </div>
        <div class="header-top"
        v-show="!showHeader"
        :style="styleOpacity">
            <div class="header-left">
            <span class="iconfont" @click="toHome">&#xe658;</span>
        </div>
        北京国际鲜花港
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            showHeader: true,
            styleOpacity: {
                opacity: 0
            }
        }
    },
    methods:{
        toHome() {
            this.$router.push("/")
        }
    },
    mounted() {
        let that = this;
        window.addEventListener("scroll", function(){
            let top = this.document.documentElement.scrollTop;
            if(top>45){
                let opacity = top/130;
                opacity=opacity>1?1:opacity
                that.styleOpacity={opacity}
                that.showHeader = false
            }else{
                that.showHeader = true
            }
        })
    }
    
}
</script>
<style scoped lang='stylus'>
@import '~css/var.styl'
.header-return {
    position: absolute;
    left: .1rem;
    top: .1rem;
    width: .72rem;
    height: .72rem;
}
.border-return {
    display: block;
    background: #000;
    width: .72rem;
    height: .72rem;
    opacity: .5;
    border-radius: .36rem;
}
.return {
    position: absolute;
    left: 0;
    top: .1rem;
    color: #fff;
    width: .72rem;
    height: .72rem;
    text-align: left;
    text-indent: .10rem;
    font-size: .5rem;
    font-weight: bold;
}
.header-top {
    z-index: 99;
    position: fixed;
    top: 0;
    text-align: center;
    width: 100%;
    line-height: .88rem;
    background: $bgColor;
    color: $textColor;
    font-size: .36rem;
}
.header-left{
    position: absolute;
    left: 0;
    width: .4rem;
    padding: 0 .2rem;
    text-align: center;
    font-weight: bold;
}
</style>