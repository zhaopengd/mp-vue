<template>
  <div class="firstViewContainer">
    <!-- 小圆点的属性根据索引显示 -->
    <swiper :indicator-dots="current!==3" @change="handleChange">
      <swiper-item>
        <img src="/static/imgs/firstView/1.jpg" alt />
      </swiper-item>
      <swiper-item>
        <img src="/static/imgs/firstView/2.jpg" alt />
      </swiper-item>
      <swiper-item>
        <img src="/static/imgs/firstView/3.jpg" alt />
      </swiper-item>
      <swiper-item>
        <img src="/static/imgs/firstView/nvsheng.jpg" alt />
      </swiper-item>
    </swiper>
    <button v-if="current===3" class="goto_books" @click="tobooks">开始体验</button>
  </div>
</template>
<script>
export default {
  data() {
    return {
      current: ''
    }
  },
  methods: {
    handleChange(e) {
      //  console.log(e)
      this.current = e.target.current
    },
    tobooks() {
      // switchTab跳转到tabBar页面，并关闭其他所有非 tabBar页面 navigateTo不好使
      wx.switchTab({
        url: '/pages/books/main'
      })
    }
  }
}
</script>
<style lang="stylus" rel="stylesheet/stylus">
.firstViewContainer
  width 100%
  height 100%
  swiper
    width 100%
    height 100%
    img
      width 100%
      height 100%
  .goto_books
    width 280rpx
    height 80rpx
    font-size 30rpx
    background rgba(255, 255, 255, 0.3)
    text-align center
    line-height 80rpx
    border-radius 20rpx
    position absolute
    bottom 20rpx
    left 50%
    margin-left -140rpx
</style>
