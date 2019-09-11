<template>
  <div class="searchContainer">
    <div class="search_header">
      <input
        class="search_input"
        placeholder-class="placeholder"
        type="text"
        placeholder="书中自有颜如玉"
        v-model="searchText"
        @confirm="confirmHandle"
      />
      <!-- confirm 点击完成按钮时触发   confirm-type 规定小键盘显示搜索还是完成 -->
      <span class="clear" @click="searchText=''" v-show="searchText">X</span>
    </div>
    <BooksList :booksList="booksList" />
  </div>
</template>
<script>
import BooksList from '../booksList/index.vue'
export default {
  components: {
    BooksList
  },
  data() {
    return {
      searchText: '',
      booksList: []
    }
  },
  methods: {
    confirmHandle() {
      // 1 收集输入内容
      const searchText = this.searchText
      // 2 发送请求
      const url = `http://localhost:3000/searchBooks`
      wx.request({
        url,
        data: {
          req: { req: searchText }
        },
        success: req => {
          console.log(req.data)
          this.booksList = req.data
        },
        fail: () => {
          console.log('失败了')
        }
      })
    }
  }
}
</script>
<style lang="stylus" rel="stylesheet/stylus">
.searchContainer
  .search_header
    border-bottom 1rpx solid #02a774
    width 80%
    margin 0 auto
    height 80rpx
    position relative
    .search_input
      height 100%
      .placeholder
        color #02a774
        text-align center
        font-size 28rpx
    .clear
      position absolute
      font-size 28rpx
      color #02a774
      right 28rpx
      top 20rpx
      z-index 99
</style>
