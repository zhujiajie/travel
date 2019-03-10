<template>
  <div>
    <home-header :city="city"></home-header>
    <homeSwiper :list="swiperList"></homeSwiper>
    <homeIcons :list="iconList"></homeIcons>
    <homeRecommend :list="recommendList"></homeRecommend>
    <homeWeekend :list="weekendList"></homeWeekend>
  </div>
</template>

<script>
import homeHeader from './components/header'
import homeSwiper from './components/Swiper'
import homeIcons from './components/icons'
import homeRecommend from './components/recommend'
import homeWeekend from './components/weekend'
import axios from 'axios'
export default {
  name: 'home',
  components: {
    homeHeader,
    homeSwiper,
    homeIcons,
    homeRecommend,
    homeWeekend
  },
  data() {
    return {
      city:'',
      swiperList:[],
      iconList:[],
      recommendList:[],
      weekendList:[]
    }
  },
  methods: {
    getHomeInfo(){
      axios.get('/api/index.json')
      .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      res=res.data;
      if(res.ret&&res.data){
        const data=res.data;
        this.city=data.city;
        this.swiperList=data.swiperList;
        this.iconList=data.iconList;
        this.recommendList=data.recommendList;
        this.weekendList=data.weekendList;
      }
      // console.log(res);
    }
  },
  mounted () {
    this.getHomeInfo()
  }
}
</script>

<style>

</style>
