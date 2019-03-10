<template>
    <div>
        <cityHeader></cityHeader>
        <citySearch></citySearch>
        <cityList :cities="cities" :hotCities="hotCities"></cityList>
        <cityAlphabet :cities="cities"></cityAlphabet>
    </div>
</template>

<script>
import axios from 'axios'
import cityHeader from './components/header'
import citySearch from './components/search'
import cityList from './components/list'
import cityAlphabet from './components/alphabet'
export default {
    name:'City',
    components:{
        cityHeader,
        citySearch,
        cityList,
        cityAlphabet
    },
    data () {
        return {
            cities:{},
            hotCities: []
        }
    },
    methods : {
        getCityInfo () {
            axios.get('/api/city.json')
                .then(this.getCityInfoSucc)
        },
        getCityInfoSucc (res){
            // console.log(res)
            res=res.data;
            if(res.ret&&res.data){
                const data=res.data
                this.cities=data.cities
                this.hotCities=data.hotCities
            }
        }
    },
    mounted () {
        this.getCityInfo()
    }
}
</script>

<style lang="stylus" scoped>

</style>
