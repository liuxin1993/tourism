<template>
	<div class="city" ref="wrapper">
		<div>
			<div class="city-box">
				<div class="title">当前城市</div>
				<div class="city-lsit">
					<div class="city-cont">
						<div class="city-name">{{this.city}}</div>
					</div>
				</div>
			</div>
			<div class="city-box">
				<div class="title">热门城市</div>
				<div class="city-lsit">
					<div class="city-cont" v-for="item of hotCities" :key="item.id" @click="handleCity(item.name)">
						<div class="city-name">{{item.name}}</div>
					</div>
				</div>
			</div>
			<div class="name-list">
				<div class="city-box" v-for="(city, key) of cities" :key="key" :ref="key">
					<div class="title">{{key}}</div>
					<ul class="dq-list">
						<li class="dq-name" v-for="item of city" :key="item.id" @click="handleCity(item.name)">{{item.name}}</li>
					</ul>
				</div>
				
			</div>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	import { mapState, mapMutations } from 'vuex'
	export default {
		name:'ListCity',
		props:{
			hotCities:Array,
			cities:Object,
			letter:String
		},
		computed:{
			...mapState(['city'])
		},
		methods:{
			handleCity(city){
				this.changeCity(city)
				this.$router.push('/')
			},
			...mapMutations(['changeCity'])
		},
		mounted () {
			this.scroll = new BScroll(this.$refs.wrapper)			
		},
		watch:{
			letter(){
				this.scroll.scrollToElement(this.$refs[this.letter][0])
			}
		}
	}
</script>

<style lang="stylus" scoped>
	.city
		position:absolute
		left:0
		right:0
		bottom:0
		top:1.6rem
		overflow:hidden
		.title
			font-size:.3rem
			line-height:.6rem
			padding-left:.2rem
			background:#eee
			color:#666
		.city-lsit		
			overflow:hidden
			padding-right:.5rem
			.city-cont
				width:33.33%
				float:left
				box-sizing:border-box
				padding:.1rem
				margin-top:.1rem
				.city-name
					font-size:.3rem
					line-height:.5rem
					border:1px solid #ddd
					text-align:center
		.dq-list			
			.dq-name
				padding-left:.2rem
				line-height:.7rem
				font-size:.3rem
				color:#666
				border-bottom:1px solid #ddd		
</style>