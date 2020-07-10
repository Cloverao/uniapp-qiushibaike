<template>
	<view class="user-list c_flex c_flex_a_c animated bounceInRight fast" @tap="opendetail">
	  
	    <image :src="item.userpic" mode="widthFix" lazy-load></image>
	    <view>
	      <view>{{item.username}}</view>
	      <view style="display: inline-block;">
	        <tag-sex-age :sex="item.sex" :age="item.age"></tag-sex-age>
	      </view>
	    </view>
	    <!-- <view class="icon iconfont icon-xuanze-yixuan"></view> -->
	    <view class="icon iconfont " :class="[item.isguanzhu?'icon-xuanze-yixuan' : 'icon-zengjia1']"></view>
	  
	  
	</view>
</template>

<script>
  import tagSexAge from "@/components/my/common/tag-sex-age.vue"
	export default {
    components:{
      tagSexAge
    },
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
          url:"../../pages/user-chart/user-chart"
        })
      },
		}
	}
</script>

<style scoped>
.user-list {
    padding: 20upx 0;
    border-bottom: 1px solid #EEEEEE;
  }

  .user-list>image {
    width: 100upx;
    border-radius: 100%;
    margin-right: 20upx;
    flex-shrink: 0;
  }

  .user-list>view:first-of-type {
    flex: 1;
  }

  .user-list>view:last-child {
    color: #CCCCCC;
  }

  .user-list>view:first-of-type>view:first-child {
    font-size: 32upx;
  }

  .user-list>view:last-of-type {
    width: 80upx;
  }
  .icon-zengjia1{
    color: #F0AD4E !important;
  }
</style>
