<template>
	<view class="uni-tab-bar">
	    <scroll-view scroll-x class="uni-swiper-tab" :style="scrollStyle">
	        <block v-for="(item,index) in  tabBars" :keys="index">
	            <view class="swiper-tab-list" :class="{'active':tabIndex == index}" @tap="tabtap(index)" :style="scrollItemStyle">{{item.name}}
              {{item.num ? item.num :''}}
	            <view class="swiper-tab-line"></view>
	            </view>
	        </block>
	    </scroll-view>
	</view>
</template>

<script>
	export default {
        props:{
        	tabBars:Array,
        	tabIndex:Number,
          scrollStyle:{
            type:String,
            default:''
          },
          scrollItemStyle:{
            type:String,
            default:''
          }
        },
		data() {
			return {
				
			}
		},
		methods: {
			tabtap(index)   {
			    // this.tabIndex = index
                this.$emit("tabtap",index)
			},
		}
	}
</script>

<style>
  .uni-swiper-tab{
        border-bottom: 1px solid #EEEEEE;
    }
    .swiper-tab-list{
        color:#969696;
        font-weight: bold;
    }
    .swiper-tab-list.active{
        color: #343434;
    }
    .active .swiper-tab-line{
        border-bottom: 5upx solid #FEDE33;
        margin: auto;
        width:70upx;
        border-radius: 20upx;
        border-top: 5upx solid #FEDE33;
    }
</style>
