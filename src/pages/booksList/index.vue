
<template>
  <div class="bookListContainer">
    <ul>
      <li v-for="(book,index) in booksList" :key="index">
        <img :src="book.image" alt />
        <div class="book_content">
          <p>{{book.title}}</p>
          <p>{{book.author}}</p>
          <p>{{book.publisher}}</p>
        </div>
        <p class="book_price">{{book.price}}</p>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: ['booksList']
}
</script>
<style lang="stylus" rel="stylesheet/stylus">
.bookListContainer
  li
    display flex
    padding 10rpx
    border-bottom 1rpx solid #eee
    img
      width 140rpx
      height 140rpx
      margin-right 20rpx
    .book_content
      width 65%
      p
        font-size 32rpx
    .book_price
      font-size 40rpx
      font-weight 700
      color red
</style>
