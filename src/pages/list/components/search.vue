<template>
	<div>
		<div class="search">
			<input v-model="keyword" class="input-search" type="text" placeholder="请输入城市名或拼音" />
		</div>
		<div class="search-list" ref="wrapper" v-show="keyword">
			<ul class="list">
				<li class="list-name" v-for="item of list" :key="item.id">{{item.name}}</li>
				<li class="list-name" v-if="hasNoData">未找到相应结果</li>
			</ul>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	export default {
		name:'ListSearch',
		props:{
			cities:Object
		},
		data () {
			return {
				keyword:'',
				list:[]
			}
		},
		mounted () {
			this.scroll = new BScroll(this.$refs.wrapper)
		},
		watch:{
			keyword(){
				if(!this.keyword){
					this.list = []
					return
				}				
				let result = []
				for(let i in this.cities){
					this.cities[i].forEach((value, index) => {
						if(value.name.indexOf(this.keyword) > -1 || value.spell.indexOf(this.keyword) > -1){
							result.push(value)
						}
					})
				}
				this.list = result
			}
		},
		computed:{
			hasNoData(){
				return !this.list.length
			}
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/public.styl'
	.search
		background:$backgroundColor
		position:fixed
		left:0
		right:0
		top:.8rem
		padding: .1rem .2rem
		.input-search
			height:.6rem
			line-height:.6rem
			width:100%
			box-sizing:border-box
			padding:0 .1rem
			text-align:center
			font-size:.22rem
			color:#999
			border-radius:.1rem
	.search-list
		position:absolute
		left:0
		top:1.6rem
		right:0
		bottom:0
		background:#fff
		z-index:10	
		overflow:hidden
		.list-name
			padding-left:.2rem
			font-size:.3rem
			line-height:.6rem
			border-bottom:1px solid #ddd
			color:#666	
</style>