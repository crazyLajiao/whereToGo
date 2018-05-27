<template>
	<div>
		<city-header></city-header>
		<city-search :cities="cities"></city-search>
		<city-list :cities="cities" :hot="hotCities" :letter="letter"></city-list>
		<city-alphapet :cities="cities" @change="handleLetterChange"></city-alphapet>
	</div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphapet from './components/Alphapet'

export default {
	name: 'City',
	components: {
		CityHeader,
		CitySearch,
		CityList,
		CityAlphapet
	},
	data () {
		return {
			cities: {},
			hotCities: [],
			letter: ''
		}
	},
	methods: {
		getCityInfo () {
			axios.get('api/city.json').then(this.getCityInfoSucc)
		},
		getCityInfoSucc (res) {
			res = res.data
			if(res.ret && res.data){
				let data = res.data
				this.cities = data.cities
				this.hotCities = data.hotCities
			}
		},
		handleLetterChange (letter) {
			this.letter = letter
		}
	},
	mounted () {
		this.getCityInfo()
	}
}
</script>

<style>
	
</style>