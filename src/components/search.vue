<template>
  <view class="search">
    <navigator  class="searchBar">搜索</navigator>
  </view>
</template>

<script>
export default {
  name: "search.vue"
}
</script>

<style lang="scss">
.search{
  width: 750rpx;
  height: 90rpx;
  background-color: #d73c33;
  display: flex;
  justify-content: center;
  align-items: center;
.searchBar{
  width: 720rpx;
  height: 60rpx;
  line-height: 60rpx;
  background-color: #fff;
  color: #999999;
  text-align: center;
  border-radius: 30rpx;
  font-size: 28rpx;
}
}
</style>