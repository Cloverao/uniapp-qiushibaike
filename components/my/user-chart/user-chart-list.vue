<template>
	<view class="user-chart-item">
		<view v-if="item.gstime" class="user-chart-time c_flex c_flex_j_c">{{item.gstime}}</view>
		<view class="user-chart-list c_flex " :class="{'user-chart-me' : item.isme}">
		  <image :src="item.userpic" mode="widthFix" lazy-load></image>
		  <view class="user-chart-list-body">
		    <text v-if="item.type=='text'">{{item.data}}</text>
		    <image v-if="item.type=='img'" :src="item.data" mode="widthFix" lazy-load></image>
		  </view>
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
			
		}
	}
</script>

<style scoped>
.user-chart-list {
    padding: 20upx 0;
  }

  .user-chart-list>image {
    width: 100upx;
    border-radius: 100%;
    flex-shrink: 0;
  }

  .user-chart-list-body {
    background-color: #F4F4F4;
    position: relative;
    padding: 25upx;
    margin-left: 20upx;
    border-radius: 20upx;
    margin-right: 100upx;
  }

  .user-chart-list-body:after {
    position: absolute;
    top: 30upx;
    left: -30upx;
    right: 0;
    content: '';
    width: 0;
    height: 0;
    border: 16upx solid #F4F4F4;
    border-color: transparent #f4f4f4 transparent transparent;
  }

  .user-chart-me {
    flex-direction: row-reverse;
  }

  .user-chart-list-body>image {
    max-width: 300upx;
    max-height: 300upx;
  }

  .user-chart-me .user-chart-list-body {
    margin-right: 20upx;
    margin-left: 100upx;
  }

  .user-chart-me .user-chart-list-body:after {
    left: auto;
    right: -30upx;
    border-color: transparent transparent transparent #f4f4f4;
  }

  .user-chart-time {
    padding: 10upx 0;
    color: #a2a2a2;
    font-size: 24upx;
  }
</style>
