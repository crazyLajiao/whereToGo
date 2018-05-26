<template>
	<div>
		<div class="title">周末去哪儿</div>
		<ul>
			<li class="item border-bottom" v-for="item of weekendList" :key="item.id">
				<div class="item-img-wrapper">
					<img class="item-img" :src="item.imgUrl">
				</div>
				<div class="item-info">
					<p class="item-title">{{item.title}}</p>
					<p class="item-desc">{{item.desc}}</p>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
export default {
	name: 'HomeWeekend',
	data () {
		return {
			weekendList: [
			{id:'001',imgUrl:'http://img1.qunarzz.com/sight/source/1510/6e/1ea71e2f04e.jpg_r_640x214_aa6f091d.jpg',title:'北京温泉排行榜',desc:'细数北京温泉，温暖你的冬天'},
			{id:'002',imgUrl:'http://img1.qunarzz.com/sight/source/1505/ce/bc89bc2f0e33ea.jpg_r_640x214_3e408453.jpg',title:'故宫',desc:'东方宫殿建筑代表，世界宫殿建筑典范'},
			{id:'003',imgUrl:'http://img1.qunarzz.com/sight/source/1510/6e/1ea71e2f04e.jpg_r_640x214_aa6f091d.jpg',title:'故宫',desc:'东方宫殿建筑代表，世界宫殿建筑典范'},
			]
		}
	}
	
}
</script>

<style lang='stylus' scoped>
@import '~styles/mixins.styl'
.title
	line-height: .8rem
	background: #eee
	text-indent: .2rem
.item-img-wrapper
	overflow: hidden
	height: 0
	padding-bottom: 37.09%
	.item-img
		width: 100%
.item-info
	padding: .1rem
	.item-title
		line-height: .54rem
		font-size: .32rem
		ellipsis()
	.item-desc
		line-height: .4rem
		color: #ccc
		ellipsis()
</style>