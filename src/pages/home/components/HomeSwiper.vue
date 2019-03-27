<template>
	<div class="pic">
		<swiper :options="swiperOption" v-if="show">
		    <swiper-slide v-for="item of swiperList" :key="item.id">
		    	<img class="swiper_img" :src="item.imgUrl">
		    </swiper-slide>
		    <div class="swiper-pagination"  slot="pagination"></div>
		</swiper>
	</div>
</template>

<script>
	export default {
		name:'HomeSwiper',
		props:{
			swiperList:Array
		},
		data () {
			return {
				swiperOption:{
					pagination:'.swiper-pagination',
					loop:true
				}
			}
		},
		computed:{
			show(){
				return this.swiperList.length
			}
		}
	}
</script>

<style lang="stylus" scoped>
	.pic>>>.swiper-pagination-bullet-active
		background:#fff
	.pic
		width:100%
		height:0
		padding-bottom:31.2%
		overflow:hidden
		.swiper_img
			width:100%
</style>