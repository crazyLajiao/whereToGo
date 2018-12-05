<template>
    <div class="city">
        <city-header></city-header>
        <city-search :cities="cities"></city-search>
        <city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
        <city-alphabet :cities="cities" @change="handleLetterChange"></city-alphabet>
    </div>
</template>

<script>
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'
import axios from 'axios'

export default {
    data() {
        return {
            cities: {},
            hotCities: [],
            letter: ''
        }
    },
    components: {
        CityHeader,
        CitySearch,
        CityList,
        CityAlphabet
    },
    methods: {
        getCityInfo() {
            axios.get('https://www.easy-mock.com/mock/5c0714f95054d376e455c604/kuniu/city').then(this.getCityInfoSucc)
        },
        getCityInfoSucc(res) {
            res = res.data
            if(res.ret && res.data) {
                const data = res.data
                this.cities = data.cities
                this.hotCities = data.hotCities
            }
              console.log(res)
        },
        handleLetterChange(letter) {
            this.letter = letter
            // console.log(letter)
        }
    },
    mounted() {
        this.getCityInfo()
    }
}
</script>
<style lang="stylus" scoped>

</style>
