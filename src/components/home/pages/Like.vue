<template>
    <div class="like">
        <div class="like-top">
            <!-- <img src="@/assets/img/like.png"> -->
            猜你喜欢
        </div>
        <ul>
            <li class="like-item border-bottom"
            v-for="item in likeList"
            :key="item.id"
            @click="toDetails">
                <div class="like-img">
                    <img :src=item.imgUrl>
                </div>
                <div class="like-text">
                    <div class="like-title">
                        {{item.title}}
                    </div> 
                    <div class="like-message">
                        {{item.msg}}
                    </div>
                    <div class="like-map">
                        <span class="like-mark">￥<b>{{item.pre}}</b></span>起
                        <span class="like-item-map">{{item.map}}</span>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
export default {
    props:['likeList'],
    data () {
        return {
        }
    },
    methods: {
        toDetails() {
            this.$router.push("/detail")
        }
    }
}
</script>
<style scoped>
.like {
    margin-top: .2rem;
    font-size: .28rem;
    background: #fff;
    padding: 0 .2rem;
}
.like-top {
    padding: .2rem 0;
    font-size: .32rem;
}
.like-top img {
    width: .3rem;
    height: .3rem;
}
.like-item {
    position: relative;
    padding: .2rem 0;
    overflow: hidden;
}
.like-img {
    float: left;
}
.like-item img {
    width: 2rem;
    height: 2rem;
}
.like-text {
    overflow: hidden;
    padding-left: .22rem;
}
.like-title {
    font-size: .36rem;
    color: #212121;
    margin-top: .4rem;
}
.like-message {
    margin-top: .3rem;
    color: #616161;
    font-size: .24rem;
}
.like-map {
    margin-top: .3rem;
    color: #616161;
    position: relative;
}
.like-mark {
    color: #ff8300;
}
.like-mark b {
    font-size: .4rem;
}
.like-item-map {
    font-size: .28rem;
    position: absolute;
    right: 0;
    top: .1rem;
}
</style>