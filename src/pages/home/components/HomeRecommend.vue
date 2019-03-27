<template>
	<div>
		<div class="recommend_tit">热销推荐</div>
		<div class="recommend_list">
			<div class="recommend_childer" v-for="item of recommendList" :key="item.id">
				<img class="recommend-img" :src="item.imgUrl">
				<div class="recommend-box">
					<div class="recommend-box-tit">{{item.title}}</div>
					<div class="recommend-desc">{{item.desc}}</div>
					<div class="recommend-detail">查看详情</div>
				</div>
			</div>
			
		</div>
	</div>
</template>

<script>
	export default {
		name:'HomeRecommend',
		props:{
			recommendList:Array
		}
	}
</script>

<style lang="stylus" scoped>
	.recommend_tit
		line-height:.6rem
		height:.6rem
		font-size:.3rem
		color:#333
		background:#ddd
		padding-left:.2rem
		margin-top:.1rem
		
	.recommend_childer
		padding:.2rem		
		display:flex
		.recommend-img
			width:1.5rem
			height:1.5rem
		.recommend-box
			flex:1
			margin-left:.2rem
			.recommend-box-tit
				line-height:.5rem
				font-size:.3rem
				color:#333
			.recommend-desc
				line-height:.4rem
				font-size:.2rem
				height:.4rem
				overflow:hidden
				white-space:nowrap
				text-overflow:ellipsis
				color:#999
			.recommend-detail
				width:1.5rem
				text-align:center
				line-height:.5rem
				height:.5rem
				border-radius:.1rem
				background:#ff9300
				color:#fff
				margin-top:.1rem
		
</style>