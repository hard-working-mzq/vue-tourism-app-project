<template>
    <div ref="container" class="container">
        <div>
        <!-- hot -->
            <div class="hot">
            <div class="hot-title">热门城市</div>
            <ul class="hot-list">
                <li class="hot-item" v-for="item in hotCities"
                :key="item.id"
                @click="changeCityName(item.name)">{{item.name}}</li>
            </ul>
            </div>
            <!-- sort -->
            <div class="sort">
            <div class="sort-title">字母排序</div>
            <ul class="sort-list">
                <li class="sort-item" v-for="(val, key) in cities" 
                @click="changeSort(key)"
                :key="key">{{key}}</li>
            </ul>
            </div>
            <!-- list -->
            <div class="list">
                <div  v-for="(val, key) in cities" 
                :ref="key"
                :key="key">
                    <div class="list-title">{{key}}</div>
                    <ul class="list-msg">
                    <li class="list-item" v-for="item in val"
                    :key="item.id"
                    @click="changeCityName(item.name)">{{item.name}}</li>
                </ul>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { mapMutations } from 'vuex'
import BetterScroll from 'better-scroll'
export default {
    props: ['hotCities','cities'],
    data() {
        return {
            scroll: ''
        }
    },
    mounted() {
        let container = this.$refs['container'];
        this.scroll = new BetterScroll(container, {
            movable: true,
            zoom: true
            })
    },
    methods: {
        changeSort(sortName) {
            this.scroll.scrollToElement(this.$refs[sortName][0])
        },
        changeCityName(cityName) {
            this.changeCity(cityName);
            this.$router.push('/')
        },
        ...mapMutations(['changeCity'])
    }
}
</script>
<style scoped lang="stylus">
@import '~css/common.styl';
.container {
    position: absolute;
    overflow: hidden;
    left: 0;
    right: 0;
    bottom: 0;
    top: .88rem;
    background: #f5f5f5;
}
.hot-title {
    font-size: .24rem;
    color: #212121;
    padding: .2rem .3rem;
}
.hot-list {
    position: relative;
    overflow: hidden;
    background: #fff;
    font-size: .28rem;
    color: #212121;
}
.hot-list:before {
    content: "";
    position: absolute;
    height: 100%;
    width: 33.33333%;
    left: 33.33333%;
    border-left: .02rem solid #ddd;
    border-right: .02rem solid #ddd;
}
.hot-item {
    position: relative;
    width: 33.33333%;
    text-align: center;
    height: .9rem;
    line-height: .9rem;
    float: left;
    border-bottom: .02rem solid #ddd;
}
.sort-title{
	font-size:.24rem;
	color:#212121;
	padding:.2rem .3rem;
}
.sort-list{
	position: relative;
	overflow: hidden;
	background: #fff;
	font-size:.28rem;
	color:#212121;
}
.sort-item{
	width:16.66666%;
	text-align: center;
	height:.9rem;
	line-height: .9rem;
	float:left;
}
.list-title {
    font-size: .24rem;
    color: #212121;
    padding: .2rem .3rem;
}
.list-msg {
    position: relative;
    background: #fff;
    overflow: hidden;
}
.list-msg:before {
    content: "";
    position: absolute;
    height: 100%;
    width: 25%;
    left: 25%;
    border-left: .02rem solid #ddd;
    border-right: .02rem solid #ddd;
}
.list-msg:after {
    content: "";
    position: absolute;
    height: 100%;
    width: 0%;
    left: 75%;
    border-left: .02rem solid #ddd;
}
.list-item {
    position: relative;
    width: 25%;
    font-size: .28rem;
    text-align: center;
    line-height: .9rem;
    float: left;
    border-bottom: .02rem solid #ddd;
    textOverflow();
}
</style>