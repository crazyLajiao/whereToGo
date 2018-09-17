<template>
    <div>
        <div class="item" v-for="(item,index) in list" :key="index">
            <div class="item-title border-bottom" @click="toggleClick">
                <span class="item-title-icon"></span>
                {{item.title}}
                <span class="item-more" v-show="item.children">更多>></span>
                <span class="item-price">￥{{item.price}}起</span>
            </div>
            <div v-show="toggleShow" v-if="item.children" class="item-chilren">
                <detail-list :list="item.children"></detail-list>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'DetailList',
    props: {
        list: Array
    },
    data() {
        return {
            toggleShow: false
        }
    },
    methods: {
        toggleClick() {
            this.toggleShow = !this.toggleShow
        }
    }
}
</script>
<style lang="stylus" scoped>
  .item-title-icon
    position: relative
    left: .06rem
    top: .06rem
    display: inline-block
    width: .36rem
    height: .36rem
    background: url(http://s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat
    margin-right: .1rem
    background-size: .4rem 3rem
  .item-title
    line-height: .8rem
    font-size: .32rem
    padding: 0 .2rem
    .item-more
        float: right
        font-size: .24rem
    .item-price
        float: right
        color: orange
        margin-right: .2rem
  .item-chilren
    padding: 0 .2rem
</style>