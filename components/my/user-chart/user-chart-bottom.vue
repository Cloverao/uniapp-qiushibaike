<template>
	<view class="user-chat-bottom c_flex c_flex_j_sb c_flex_a_c">
	  <input type="text" placeholder="文明发言" v-model="text"/>
	  <view class="icon iconfont icon-fabu" @tap="submit"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text:''
			}
		},
		methods: {
			// changeInput(){
   //      this.$emit("changeInput",this.text)
   //    },
      submit() {
        this.$emit("submit",this.text)
        this.text = '';
      },
		}
	}
</script>

<style scoped>
.user-chat-bottom {
    position: fixed;
    bottom: 0;
    left: 0;
    right: 0;
    height: 100upx;
    padding: 0upx 20upx;
    border-top: 1upx solid #EEEEEE;
    display: flex;
  }

  .user-chat-bottom>input {
    border: 1upx solid #EEEEEE;
    flex: 1;
    margin-right: 20upx;
    border-radius: 10upx;
    height: 35upx;
    line-height: 235upx;
    font-size: 30upx;
    background-color: #F7F7F7;
    padding: 10upx 0;
    text-indent: 25upx;
  }

  .user-chat-bottom>view {
    width: 80upx;
    font-size: 35upx;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>
