<template>
  <div class="header">
    <div class="header-left">
      <div class="iconfont back-icon">&#xe624;</div>
    </div>
    <div class="header-input">
      <span class="iconfont">&#xe632;</span>
      输入城市游玩主题
    </div>
    <router-link to="/city">
      <div class="header-right">
        {{this.city}}
        <span class="iconfont arrow-icon">&#xe64a;</span>
      </div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'homeHeader',
  props:{
    city:String
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/varibles.styl';
  .header
    display: flex
    height: $headerHeight
    background: $bgcolor
    line-height: $headerHeight
    color:#fff
    .header-left
      width: .64rem
      float: left
      .back-icon
        font-size .4rem
        text-align center
    .header-input
      flex: 1
      margin-top .12rem
      height .64rem
      margin-left .2rem
      background:#fff
      border-radius .1rem
      line-height .64rem
      color #ccc
      padding-left .2rem
    .header-right
      width: 1.24rem
      float: right
      text-align center
      color #fff
      .arrow-icon
        margin-left -.04rem
        font-size .24rem
</style>
