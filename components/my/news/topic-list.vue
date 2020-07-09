<template>
	<view class="topic-list c_flex animated bounceInRight fast" @tap="opendetail">
	  <image :src="item.titlepic" mode="widthFix" lazy-load></image>
	  <view>
	    <view>#{{item.title}}#</view>
	    <view>{{item.desc}}</view>
	    <view>动态 {{item.totalnum}} 今日 {{item.todaynum}}</view>
	  </view>
	</view>
</template>

<script>
	export default {
    props:{
      item:Object,
      index:Number
    },
		data() {
			return {
				
			}
		},
		methods: {
			opendetail(){
        uni.navigateTo({
          url:"../../pages/topic-detail/topic-detail"
        })
      },
		}
	}
</script>

<style scoped>
.topic-new{
      padding:20upx;
    }
    .topic-new>view:first-child{
      padding-bottom:20upx ;
      font-size: 32upx;
    }
    .topic-list{
      padding:20upx 0;
      border-bottom: 1upx solid #EEEEEE;
      margin-bottom: 10upx;
    }
    .topic-list>image{
      width: 200upx;
      border-radius: 15upx;
      margin-right: 20upx;
    }
    .topic-list>view>view:first-child{
      font-size: 32upx;
      color: #333333;
    }
    .topic-list>view>view:not(:first-child){
      color: #a4a4a4;
      font-size: 27upx;
    }
</style>
