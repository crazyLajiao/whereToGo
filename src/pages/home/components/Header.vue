<template>
	<div class="header">
		<div class="header-left">
			<div class="iconfont back-icon">&#xe624;</div>
		</div>
		<div class="header-input">
			<span class="iconfont">&#xe632;</span>
			输入城市、游玩、主题
		</div>
		<router-link to="/city">
			<div class="header-right">
				合肥
				<span class="iconfont arrow-icon">&#xe64a;</span>
			</div>
		</router-link>
	</div>
</template>
<script>
export default {
	name: 'HomeHeader'
}
</script>

<style lang="stylus" scoped>
	@import '~styles/varibles.styl'
	.header
		display: flex
		line-height: $headerHeight
		background: $bgColor
		color: #fff
		.header-left
			width: .64rem
			float: left
			margin-top: -.1rem
			.back-icon
				text-align: center
				margin-top: .22rem
				font-size: .4rem
		.header-input
			flex: 1
			height: .64rem
			line-height: .64rem
			margin-top: .19rem
			margin-left: .2rem
			padding-left: .2rem
			background: #fff
			color: #ccc
			border-radius: .1rem
		.header-right
			min-width: 1.04rem
			padding: 0 .1rem
			float: right
			text-align: center
			margin-top: .12rem
			color: #fff
			.arrow-icon
				margin-left: -.04rem
				font-size: .2rem
</style>
