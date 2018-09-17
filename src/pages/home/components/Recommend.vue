<template>
    <div>
        <div class="title">热销推荐</div>
        <ul>
            <router-link tag="li" class="item" v-for="item in list" :key="item.id" :to="'/detail/'+item.id">
                <img class="item-img" :src='item.imgUrl'>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <star :score="item.score" :size="24" class="item-star"></star>
                    <span class="item-comment">{{item.comments}}条评论</span>
                    <p></p>
                    <p  class="item-price"><span class="price">￥{{item.price}}</span>起</p>
                    <span  class="item-location">{{item.location}}</span>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </router-link>
        </ul>
    </div>
</template>
<script>
import Star from 'common/star/Star'

export default {
    name: 'HomeRecommend',
    props: {
        list: Array
    },
    components: {
        Star
    }
}
</script>

<style lang="stylus" scoped>
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
      .item-star,.item-comment,.item-price,.item-location
        font-size: .24rem
      .item-star
        display: inline-block
      .item-comment
        margin-right: .2rem
      .item-price 
        margin-top: .1rem
        margin-bottom: .1rem
        display: inline-block
        .price
          margin-right: .1rem
          font-size: .32rem
          color: orange
      .item-location
          margin-top: .1rem
          margin-bottom: .1rem
          float:right
          margin-right: .2rem
      .item-desc
        line-height: .4rem
        color: #ccc
        ellipsis()
</style>
