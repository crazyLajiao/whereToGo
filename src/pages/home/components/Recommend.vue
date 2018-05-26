<template>
	<div>
		<div class="title">热门推荐</div>
		<ul>
			<li class="item border-bottom" v-for="item of recommendList" :key="item.id">
				<img class="item-img" :src="item.imgUrl">
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
					<button class="item-button">查看详情</button>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'HomeRecommend',
	data () {
		return {
			recommendList: [
			{id:'001',imgUrl:'http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_140x140_80f63803.jpg',title:'故宫',desc:'东方宫殿建筑代表，世界宫殿建筑典范'},
			{id:'002',imgUrl:'http://img1.qunarzz.com/sight/p0/1501/f4/f467729126949c3a.water.jpg_140x140_ef235b1c.jpg',title:'故宫',desc:'东方宫殿建筑代表，世界宫殿建筑典范'},
			{id:'003',imgUrl:'http://img1.qunarzz.com/sight/p0/1501/40/40b2b6c951b28fdd.water.jpg_140x140_1c863e5c.jpg',title:'故宫',desc:'东方宫殿建筑代表，世界宫殿建筑典范'},
			]
		}
	}
}
</script>

<style lang='stylus' scoped>
	@import '~styles/mixins.styl'
	.title
		margin-top: .2rem
		line-height: .8rem
		background: #eee
		text-indent: .2rem
	.item
		overflow: hidden
		display: flex
		height: 1.9rem
		.item-img
			width: 1.7rem
			height: 1.7rem
			padding: .1rem
		.item-info
			flex: 1
			padding: .1rem
			min-width: 0
			.item-title
				line-height: .54rem
				font-size: .32rem
				ellipsis()
			.item-desc
				line-height: .4rem
				color: #ccc
				ellipsis()
			.item-button
				line-height: .44rem
				margin-top: .16rem
				background: #ff9300
				padding: 0 .2rem
				border-radius: .06rem
				color: #fff
</style>