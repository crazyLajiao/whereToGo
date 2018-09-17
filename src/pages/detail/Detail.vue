<template>
    <div>
        <detail-banner :imgs="gallaryImgs" :sightName="sightName" :bannerImg="bannerImg"></detail-banner>
        <detail-header></detail-header>
        <div class="content">
            <div class="buyTicks">购票</div>
            <detail-list :list="list"></detail-list>
        </div>
        <detail-comment></detail-comment>
    </div>
</template>
<script>
import axios from 'axios'
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import DetailComment from './components/Comment'

export default {
    name: 'Detail',
    data() {
        return {
            sightName: '',
            bannerImg: '',
            gallaryImgs: [],
            list: []
        }
    },
    components: {
        DetailBanner,
        DetailHeader,
        DetailList,
        DetailComment
    },
    methods: {
        getDetailInfo() {
            // axios.get('/api/detail.json?id='+this.$router.params.id).then(this.getDetailInfoSucc)
            axios.get('/api/detail.json',{
                params: {
                    id: this.$route.params.id
                }
            }).then(this.getDetailInfoSucc)
        },
        getDetailInfoSucc(res) {
            res = res.data
            if(res.ret && res.data) {
                const data = res.data
                this.sightName = data.sightName
                this.bannerImg = data.bannerImg
                this.gallaryImgs = data.gallaryImgs
                this.list = data.categoryList
                // console.log(data)
            }
        }
    },
    mounted() {
        this.getDetailInfo()
    }
}
</script>
<style lang="stylus" scoped>
    .content
        .buyTicks
            line-height: .6rem
            background: #eee
            padding-left: .2rem
            color: #666
            font-size: .32rem
</style>

