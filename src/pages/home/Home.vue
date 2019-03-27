<template>
	<div>
		<home-header></home-header>
		<home-swiper :swiperList="swiperList"></home-swiper>
		<home-icon :iconList="iconList"></home-icon>
		<home-recommend :recommendList="recommendList"></home-recommend>
		<home-weekend :weekendList="weekendList"></home-weekend>
	</div>
</template>

<script>
	import HomeHeader from "./components/Header"
	import HomeSwiper from './components/HomeSwiper'
	import HomeIcon from './components/HomeIcon'
	import HomeRecommend from './components/HomeRecommend'
	import HomeWeekend from './components/HOmeWeekend'
	import axios from 'axios'
	import { mapState } from 'vuex'
	export default {
		name:'Home',
		components:{
			HomeHeader,
			HomeSwiper,
			HomeIcon,
			HomeRecommend,
			HomeWeekend
		},
		data () {
			return {
				swiperList:[],
				iconList:[],
				recommendList:[],
				weekendList:[],
				lastCity:''
			}
		},
		methods:{
			handGetInfo(){
				axios.get('./static/mock/index.json?city='+this.city).then(this.handGetInfoSucc)
			},
			handGetInfoSucc(res){
				res = res.data			
				if(res.ret&&res.data){					
					let data = res.data
					this.swiperList = data.swiperList
					this.iconList = data.iconList
					this.recommendList = data.recommendList
					this.weekendList = data.weekendList
				}
			}
		},
		mounted () {			
			this.lastCity = this.city
			this.handGetInfo()
		},
		computed:{
			...mapState(['city'])
		},
		activated(){
			if(this.lastCity != this.city){
				this.handGetInfo()
				this.lastCity = this.city
			}
		}
	}
</script>

<style>
</style>