<template>
	<div>
		<div class="icon">
			<swiper :options="swiperOption">
		    	<swiper-slide v-for="(page, index) of pages" :key="index">
					<div class="icon_childer" v-for="item of page" :key="item.id">
						<div class="icon_pic">
							<img :src="item.imgUrl">
						</div>
						<div class="icon_name">{{item.desc}}</div>
					</div>
					
				</swiper-slide>
			    <div class="swiper-pagination"  slot="pagination"></div>
			</swiper>
		</div>
	</div>
</template>

<script>
	export default {
		name:'HomeIcon',
		props:{
			iconList:Array
		},
		data () {
			return {
				swiperOption:{
					pagination:'.swiper-pagination',
					autoplay:false
				}
			}
		},
		computed:{
			pages(){
				let pages = []
				this.iconList.forEach((item, index) => {
					var page = Math.floor(index/8)
					if(!pages[page]){
						pages[page] = []
					}
					pages[page].push(item)
				})
				return pages
			}
			
		}
	}
</script>

<style lang="stylus" scoped>
	.icon
		width:100%
		height:0
		padding-bottom:50%
		overflow:hidden
		.icon_childer
			width:25%
			float:left
			padding-bottom:25%
			height:0
			overflow:hidden
			position:relative
			.icon_pic
				position:absolute
				left:0
				top:0
				right:0
				bottom:.44rem
				padding:.1rem
				img
					height:100%
					display:block
					margin:0 auto
			.icon_name
				text-align:center
				font-size:.28rem
				line-height:.44rem
				height:.44rem
				position:absolute
				left:0
				right:0
				bottom:0
				white-space:nowrap
				text-overflow:ellipsis
				overflow:hidden
</style>