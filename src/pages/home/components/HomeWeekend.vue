<template>
	<div>
		<div class="title">周末去哪儿</div>
		<div class="weekend-box" v-for="item of weekendList" :key="item.id">
			<div class="weekend-img"><img :src="item.imgUrl"></div>
			<div class="weekend-tit">{{item.title}}</div>
			<div class="weekend-desc">{{item.desc}}</div>
		</div>
		
	</div>
</template>

<script>
	export default {
		name:'HomeWeekend',
		props:{
			weekendList:Array
		}
	}
</script>

<style lang="stylus" scoped>
	.title
		font-size:.3rem
		line-height:.6rem
		padding-left:.2rem
		color:#333
		background:#ddd
	.weekend-box
		margin-top:.2rem
		.weekend-img
			img
				width:100%
		.weekend-tit
			font-size:.28rem
			line-height:.6rem
			padding-left:.2rem
		.weekend-desc
			font-size:.22rem
			color:#999
			line-height:.3rem
			padding-left:.2rem
		
</style>