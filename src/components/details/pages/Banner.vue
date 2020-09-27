<template>
    <div class="banner">
        <div @click="showSwiper">
            <div class="banner-img">
                <img src="https://imgs.qunarzz.com/vs_ceph_b2c_001/d08e9d30-a619-4a7a-b355-49030fa7fc5a.jpg_180x120x90_ce17bba6.jpg">
            </div>
            <div class="banner-title">
                金海湖风景区（AAAA景区）
            </div>
        </div>
        <div class="img-swiper"
        v-show="imgSwiper"
        @click="hideSwiper">
        <swiper :options="swiperOption">
            <swiper-slide v-for='item in bannerList' :key='item.id'>
                <img :src="item.imgUrl">
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            swiperOption: {
                pagination: {
                  el: '.swiper-pagination',
                  type: "fraction"
		        }
            },
            bannerList: [
                {
                    id:"01",
                    imgUrl:"https://imgs.qunarzz.com/vs_ceph_vs_tts/e64599b3-e35d-4981-a71f-4a77c0883571.jpg_r_390x260x95_53cccaf7.jpg"
                },
                {
                    id:"02",
                    imgUrl:"https://imgs.qunarzz.com/vs_ceph_vs_tts/ce0b9dfe-2bef-4516-9d92-eea3472b92ba.jpg_r_390x260x95_e04a6f5d.jpg"
                },
                {
                    id:"03",
                    imgUrl:"https://imgs.qunarzz.com/vs_ceph_vs_tts/2317e85b-9343-40e1-b9e7-4a492557e9a9.jpg_r_390x260x95_b143d553.jpg"
                }
            ],
            imgSwiper: false
        }
    },
    methods: {
        showSwiper() {
            this.imgSwiper = true;
        },
        hideSwiper() {
            this.imgSwiper = false;
        }
    }
}
</script>
<style scoped>
.banner {
    position: relative;
}
.banner-img {
    width: 100%;
    overflow: hidden;
    height: 0;
    padding-bottom: 55%;
}
.banner-img img {
    width: 100%;
}
.banner-title {
    position: absolute;
    bottom: .4rem;
    left: .3rem;
    font-size: .36rem;
    color: #fff;
}
.img-swiper {
    background: #000;
    position: fixed;
    top: 0;
    bottom: 0;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
}
.img-swiper img {
    width: 100%;
}
</style>