<template>
  <view>
    <view class="user-chat-bottom c_flex c_flex_j_sb">
      <input type="text" placeholder="文明发言" />
      <view class="icon iconfont icon-fabu u_flex_a_c u_flex_j_c"></view>
    </view>
  </view>
</template>

<script>
  export default {
    data() {
      return {

      }
    },
    methods: {

    }
  }
</script>

<style>
  .user-chat-bottom {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 20upx 0;
    height: 100upx;
    background-color: #FFFFFF;
    border-top: 1upx solid;

  }

  .user-chat-bottom>input {
    border: 1upx solid red;
    flex: 1;
    margin-right: 20upx;
  }

  .user-chat-bottom>view {
    background-color: yellow;
    width: 80upx;
    font-size: 35upx;
  }
</style>
