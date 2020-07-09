<template>
	<view class="toppic-nav ">
	  <view class="c_flex c_flex_j_sb">
	    <view>热门分类</view>
	    <view class="c_flex c_flex_j_sb" @tap="totoppicNav">
	      更多<view class="icon iconfont icon-jinru"></view>
	    </view>
	  </view>
	  <view class="c_flex c_flex_j_sb toppic-catrgory">
	    <block v-for="(item,index) in nav" :key="index">
	      <view>{{item.name}}</view>
	    </block>
	  </view>
	</view>
</template>

<script>
	export default {
    props:{
      nav:Array
    },
		data() {
			return {
				
			}
		},
		methods: {
			totoppicNav(){
        uni.navigateTo({
          url: '../../pages/topic-nav/topic-nav'
        });
      },
		}
	}
</script>

<style scoped>

  .swiper-item {
    width: 100%;
    display: block;
    height: 300rpx;
    line-height: 300rpx;
    text-align: center;
  }

  .swiper-list {
    margin-top: 40rpx;
    margin-bottom: 0;
  }
  .toppic-nav{
    border-bottom: 1upx solid #EEEEEE;
    border-top: 1upx solid #EEEEEE;
    padding:20upx;
  }
  .toppic-nav>view:nth-child(1){
    margin-bottom: 10upx;
  }
   .toppic-nav>view:nth-child(1)>view:last-child{
     color: #9e9e9e;
    
   }
   .toppic-nav>view:first-child>view{
      font-size: 32upx;
   }
  .toppic-catrgory>view{
    flex: 1;
    background-color:#EEEEEE ;
    color: #9e9e9e;
    border-radius: 10upx;
    margin:0 10upx;
    text-align: center;
  }
</style>
