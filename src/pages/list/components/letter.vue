<template>
	<ul class="letter">
		<li v-for="(item, key) of list" :key="key" @click="handleBtn">{{key}}</li>
	</ul>
</template>

<script>
	export default {
		name:'ListLetter',
		props:{
			list:Object
		},
		methods:{
			handleBtn(letter){
				this.$emit('changeTxt',letter.target.innerHTML)
			}
		}
	}
</script>

<style lang="stylus" scoped>
	.letter
		position:fixed
		right:0
		top:1.66rem
		bottom:0
		width:.4rem
		font-size:.3rem
		line-height:.4rem
		color:#666
		text-align:center
		display:flex
		flex-direction:column
		justify-content:center
</style>