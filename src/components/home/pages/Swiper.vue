<template>
    <div class="header-swiper">
        <swiper :options="swiperOption">
            <swiper-slide v-for='item in swiperList' :key='item.id'>
                <img :src="item.imgUrl">
            </swiper-slide>
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<script>
export default {
    props:['swiperList'],
    data () {
		return {
			swiperOption:{
				pagination: {
		          el: '.swiper-pagination'
		        },
		        loop:true
			}
		}
	}
}
</script>

<style scoped>
.header-swiper {
    background: #ccc;
    height: 0;
    padding-bottom: 21%;
}
.header-swiper img {
    width: 100%;
    height: 100%;
}
</style>