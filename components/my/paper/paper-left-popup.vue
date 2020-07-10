<template>
  <view>
    <view class="paper-left-popup-mask" v-show="show" @tap="hidepopup"></view>
    <view class="paper-left-popup" v-show="show">
      <view class="c_flex" hover-class="paper-left-popup-h" @tap="addfriend">
        <view class="icon iconfont icon-sousuo" ></view>
        加糗友
      </view>
      <view class="c_flex" hover-class="paper-left-popup-h"  @tap="clear">
        <view class="icon iconfont icon-qingchu" ></view>
        清除未读
      </view>
    </view>
  </view>
</template>

<script>
	export default {
    props:{
      show:Boolean
    },
		data() {
			return {
				
			}
		},
		methods: {
      hidepopup(){
        this.$emit("hide")
      },
			addfriend(){
			  console.log("加糗友");
			  // this.hidepopup();
        this.$emit("addfriend")
			},
			clear(){
			  console.log("清除未读");
			  // this.hidepopup();
        this.$emit("clear")
			},
		}
	}
</script>

<style scoped>
.paper-left-popup{
    position: fixed;
    right: 0;
    top:10upx;
    background-color: #FFFFFF;
    z-index: 2000;
    width:55%;
    box-shadow: 1upx 1upx 20upx #CCCCCC;
  }
  .paper-left-popup>view{
    padding:20upx;
    font-size: 30upx;
  }
   .paper-left-popup>view>view{
     margin-right:10upx;
     font-weight: bold;
   }
   .paper-left-popup-h{
     background-color: #EEEEEE;
   }
   
   .paper-left-popup-mask {
     position: fixed;
     right: 0;
     left: 0;
     top: 0;
     bottom: 0;
     z-index: 1999;
   }
</style>
