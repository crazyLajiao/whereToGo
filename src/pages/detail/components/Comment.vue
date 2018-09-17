<template>
   <div class="Comments">
        <div class="title">用户评价</div>
        <div class="button-list">
            <div class="button-wrapper">
                <div class="button" v-for="(item,index) in tagList" :key="index">
                    {{item.tagName}} {{item.tagNum}}
                </div>
            </div>
        </div>
        <div class="comment-list">
            <ul>
                <li class="comments-wrapper" v-for="item in commentList" :key="item.commentId">
                    <div class="headImg"><img class="hImg" :src="item.headImg"/></div>
                    <div class="content">
                        <span class="author">{{item.author}}</span>
                        <star :score="item.score" :size="24" class="item-star"></star>
                        <span class="date">{{item.date}}</span>
                        <div class="content-detail">
                            <p class="text">{{item.content}}</p>
                            <div class="img-wrapper">
                                <img />
                            </div>
                        </div>
                    </div>
                </li>   
            </ul>
        </div>
    </div> 
</template>
<script>
import Star from 'common/star/Star'
import axios from 'axios'

export default {
    name: 'DetailComment',
    data() {
        return {
            tagList: [],
            commentList: []
        }
    },
    components: {
        Star
    },
    methods: {
        getCommentInfo() {
            axios.get('/api/comment.json').then(this.getCommentInfoSucc)
        },
        getCommentInfoSucc(res) {
            res = res.data
            console.log(res)
            if(res.ret && res.data) {
                const data = res.data
                this.tagList = data.tagList
                this.commentList = data.commentList
            }
            //  console.log(res)
        }
    },
    mounted() {
        this.getCommentInfo()
    }
}
</script>
<style lang="stylus" scoped>
@import '~styles/mixins.styl'
    .title
        line-height: .6rem
        background: #eee
        padding-left: .2rem
        color: #666
        font-size: .32rem
    .button-list
        overflow: hidden
        padding: .1rem .6rem .1rem .1rem
        .button-wrapper
            float: left
            .button
                display: inline-block
                margin: .1rem
                padding: .2rem
                text-align: center
                background: #4d555c
                border: .02rem solid #ccc
                border-radius: .06rem
                &.active
                    background: #1E90FF
    .comment-list
        padding: 0 1rem
        .comments-wrapper
            display: flex
            padding: .18rem 0
            position: relative
            .headImg
                flex: 0 0 .58rem
                width: .58erm
                margin-right: .12rem
                .hImg 
                    width: .58rem
                    height: .58rem
                    border-radius: 50%
            .content
                position: relative
                flex: 1
                .author
                    margin-bottom: .04rem
                    line-height: .12rem
                    font-size: .1rem
                    color: #07111b
                .date
                    position: absolute
                    top: 0
                    right: 0
                    font-size: .12rem
                    color: #93999f
            .content-detail
                min-width: 0
                .text
                    display: -webkit-box
                    margin-bottom: .08rem
                    line-height: .28rem
                    color: #93999f
                    font-size: .24rem
                    -webkit-line-clamp: 3
                    -webkit-box-orient: vertical
                    overflow: hidden
                    
</style>
