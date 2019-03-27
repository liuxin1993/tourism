<template>
	<div>
		<list-header></list-header>
		<list-search :cities="cities"></list-search>
		<list-city :letter="letter" :hotCities="hotCities" :cities="cities"></list-city>
		<list-letter :list="cities" @changeTxt="hangleScroll"></list-letter>
	</div>
</template>

<script>
	import ListHeader from './components/header'
	import ListSearch from './components/search'
	import ListCity from './components/city'
	import ListLetter from './components/letter'
	import axios from 'axios'
	export default {
		name:"List",
		components:{
			ListHeader,
			ListSearch,
			ListCity,
			ListLetter
		},
		data () {
			return {
				hotCities:[],
				cities:{},
				letter:''
			}
		},
		methods:{
			handleGetInfo(){
				axios.get('./static/mock/city.json').then(this.handleGetInfpSucc)
			},
			handleGetInfpSucc(res){
				res = res.data
				if(res.ret&&res.data){
					let data = res.data
					this.hotCities = data.hotCities
					this.cities = data.cities
					console.log(data)
				}
			},
			hangleScroll(letter){
				this.letter = letter
			}
		},
		mounted(){
			this.handleGetInfo()
		}
	}
</script>

<style lang="stylus" scoped>
</style>