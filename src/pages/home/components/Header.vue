<template>
	<div class="header">
		<div class="header-l">
			<span class="iconfont header-back">&#xe624;</span>
		</div>
		<div class="header-m">
			<span class="iconfont header-search">&#xe632;</span>
			请输入城市、景点
		</div>
		<router-link to="/list">
			<div class="header-r">
				{{this.city}}
				<span class="iconfont header-down">&#xe6aa;</span>
			</div>
		</router-link>
	</div>
</template>

<script>
	import { mapState } from 'vuex'
	export default {
		name:'HomeHeader',
		computed:{
			...mapState(['city'])
		}
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/public.styl'
	.header
		height:.86rem
		line-height:.86rem
		background:$backgroundColor
		color:#fff
		text-align:center
		display:flex
		.header-l
			width:.86rem
			float:left
			.header-back
				font-size:.38rem
		.header-r
			min-width:1.2rem
			padding:0 .1rem
			float:right
			color:#fff
			.header-down
				margin-left:-.04rem
				font-size:.3rem
		.header-m
			flex:1	
			height:.66rem
			line-height:.66rem
			margin:.1rem
			background:#fff
			border-radius:.1rem
			color:#999
			text-align:left
			padding-left:.1rem
			padding-right:.1rem
			font-size:.3rem
</style>