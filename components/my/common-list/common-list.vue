<template>
	<view class="common-list c_flex animated bounceInRight fast">
	  <view class="common-list-l" >
	    <image :src="item.userpic" mode="widthFix" lazy-load></image>
	  </view>
	  <view class="common-list-r">
	    <view class="c_flex c_flex_a_c c_flex_j_sb">
	      <view class="common-list-info c_flex  ">
	        {{item.username}}
	        <!-- <view class="icon iconfont icon-nan common-list-info-age" 
	        :class="[item.sex == 0?'icon-nan' : 'icon-nv']"
	       > {{item.age}} </view> -->
         <tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
	      </view>
	      <view class="icon iconfont icon-zengjia" v-show="!isguanzhu"  @tap="guanzhu">关注</view>
	
	    </view>
	    <!--图片/视频-->
	    <view>{{item.title}}</view>
	    <view class="common-list-image c_flex c_flex_a_c c_flex_j_c" v-if="!item.share">
	
	      <image v-if="item.titlepic != ''" :src="item.titlepic" mode="widthFix" lazy-load></image>
	      <template v-if="item.video">
	        <view class="common-list-play c_flex c_flex_a_c icon iconfont icon-bofang"></view>
	        <view class="common-list-playinfo">{{item.video.looknum}} 次播放 {{item.video.long}}</view>
	      </template>
	    </view>
	    <!--分享-->
	    <view class="common-list-share c_flex c_flex_a_c" v-if="item.share">
	      <image :src="item.share.titlepic" mode="widthFix" lazy-load v-if="item.share.titlepic != ''"></image>
	      <view>{{item.share.title}}</view>
	    </view>
	    <view class="c_flex c_flex_j_sb">
	      <view>{{item.path}}</view>
	      <view class="c_flex dianzan">
	        <view class="icon iconfont icon-zhuanfa">
	          {{item.sharenum}}
	        </view>
	        <view class="icon iconfont icon-pinglun1">
	          {{item.commentnum}}
	        </view>
	        <view class="icon iconfont icon-dianzan1">
	           {{item.goodnum}}
	        </view>
	      </view>
	    </view>
	  </view>
	</view>
</template>

<script>
   import TagSexAge from "@/components/my/common/tag-sex-age.vue"
	export default {
    components:{
      TagSexAge
    },
    props:{
      item:Object,
      index:Number
    },
		data() {
			return {
				isguanzhu:this.item.isguanzhu
			}
		},
		methods: {
			guanzhu(){
        this.isguanzhu = true
        uni.showToast({
            title:"关注成功",
            mask:false,
            duration:1500
        });
      },
		}
	}
</script>

<style>
 .common-list {
    padding: 20upx;
    box-sizing: border-box;
  }

  .common-list-l {
    width: 90upx;
    height: 90upx;
    border-radius: 90upx;
    margin-right: 10upx;
    flex-shrink: 0;
  }

  .common-list-r {
    flex: 1;
    padding-bottom: 10upx;
    border-bottom: 1upx solid #EEEEEE;
  }

  .common-list-l>image {
    width: 100%;
    border-radius: 100%;
  }

  .common-list-info {
    height: 30upx;
    align-items: center;
    color: #999999;
    margin-right: 10upx;
  }


 

  .common-list-r>view:nth-child(1)>view:last-child {
    background-color: #EEEEEE;
    font-size: 25upx;
    padding: 0 10upx;
    border-radius: 5upx;
  }

  .common-list-r>view:nth-child(2) {
    font-size: 32upx;
    padding: 12upx 0;
  }

  .common-list-r>view:nth-child(3) {
    position: relative;
  }

  .common-list-play {
    position: absolute;
    color: #FFFFFF;
    font-size: 110upx;
  }

  .common-list-playinfo {
    position: absolute;
    background-color: rgba(51, 51, 51, 0.72);
    color: #FFFFFF;
    bottom: 8upx;
    right: 8upx;
    border-radius: 40upx;
    font-size: 25upx;
    padding: 0 10upx;
  }

  .common-list-share {
    background-color: #EEEEEE;
    padding: 20upx 10upx;
    font-size: 32upx;
    border-radius: 15upx;
  }

  .common-list-share>image {
    width: 180upx;
    height: 100upx;
    border-radius: 15upx;
    margin-right: 15upx;
  }

  .common-list-r>view:nth-child(4) {
    color: #999999;
  }

  .dianzan>view {
    padding: 0 10upx;
    font-size: 28upx;
  }

  .common-list-image {
    width: 100%;
  }

  .common-list-image>image {
    border-radius: 20upx;
    width: 100%;
  }
</style>
