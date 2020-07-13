<template>
	<view class="common-list c_flex animated bounceInRight fast">
	  <view class="common-list-l" >
	    <image :src="item.userpic" mode="widthFix" lazy-load></image>
	  </view>
	  <view class="common-list-r">
	    <view>
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
        <view class="common-list-r-time">
          26天前
        </view>
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
 @import "../../../common/list.css";
 .common-list-r{
   border-bottom: 0;
 }
 .common-list{
   border-bottom: 1upx solid #EEEEEE;
 }
 .common-list-r-time{
   padding:15upx 0;
   color: #CCCCCC;
   font-size: 25upx;}
   
</style>
