<template>
	<div class="header">
		<router-link to="/">
			<div class="header-back">
				<span class="iconfont">&#xe624;</span>
			</div>
		</router-link>
		城市中心
	</div>
</template>

<script>
	export default {
		name:'ListHeader'
	}
</script>

<style lang="stylus" scoped>
	@import '~styles/public.styl'
	.header
		height:.8rem
		line-height:.8rem
		text-align:center
		font-size:.32rem
		color:#fff
		background:$backgroundColor
		position:fixed
		left:0
		right:0
		top:0
		.header-back
			position:absolute
			top:0
			left:.2rem
			color:#fff
		
</style>