<template>
	<view>
		<uni-nav-bar :fixed="true" :statusBar="true" @clickRight="openAdd">
		  <block slot="left">
		    <view class="nav-left">
		      <view class="icon iconfont icon-qiandao"></view>
		    </view>
		  </block>
		  <view class="nav-tab-bar">
		    <block v-for="(item,index) in tabBars" :key="index">
		      <view :class="{'active':tabIndex == index}" @tap="changeTab(index)">
		        {{item.title}}
		        <view class="nav-tab-bar-line"></view>
		      </view>
		    </block>
		  </view>
		  <block slot="right">
		    <view class="nav-right">
		      <view class="icon iconfont icon-bianji1"></view>
		    </view>
		  </block>
		</uni-nav-bar>
	</view>
</template>

<script>
	export default {
    props:{
      tabBars:Array,
      tabIndex:Number
    },
		data() {
			return {
				
			}
		},
		methods: {
			openAdd() {
        uni.navigateTo({
          url: '../add-input/add-input'
        });
			},
      changeTab(index) {
        // this.tabIndex = index
        this.$emit('change-tab',index)
      },
		}
	}
</script>

<style>
  .nav-left>view,
  .nav-right>view {
    font-size: 40upx;
  }

  .nav-left {
    width: 80%;
    color: #ff9619;
  }

  .nav-right {
    width: 100%;
    display: flex;
    justify-content: flex-end;
  }

  .nav-tab-bar {
    display: flex;
    justify-content: center;
    width: 100%;
  }

  .nav-tab-bar view {
    padding: 0 10upx;
    font-weight: bold;
    color: #969696;
  }

  .active {
    color: #333333 !important;
  }

  .nav-tab-bar view.active .nav-tab-bar-line {
    border-bottom: 5upx solid #FEDE33;
    border-radius: 20upx;
    border-top: 5upx solid #FEDE33;
  }
</style>
