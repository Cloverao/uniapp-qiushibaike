<template>
	  <view>
      <view class="topic-bg">
        <image :src="topicInfo.titlepic" mode="aspectFill" lazy-load></image>
      </view>
      <view class="topic-info">
        <view class="topic-info-t c_flex c_flex_a_c">
          <image :src="topicInfo.titlepic" mode="widthFix" lazy-load></image>
          <view>#{{topicInfo.title}}#</view>
        </view>
        <view class="topic-info-m">
          动态 {{topicInfo.totalnum}}  今日 {{topicInfo.todaynum}} 
        </view>
        <view class="topic-info-b">
          {{topicInfo.desc}}
        </view>
      </view>
    </view>
</template>

<script>
	export default {
    props:{
      topicInfo:Object
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
 .topic-bg{
  width: 100%;
  height: 300upx;
  position: relative;
  overflow: hidden;
}
.topic-bg>image{
  width: 100%;
  position: absolute;
  filter: blur(10px);
}
.topic-info{
  padding:0 20upx;
  letter-spacing: 1upx;
}
.topic-info .topic-info-t{
  position: relative;
}
.topic-info .topic-info-t>image{
  width: 160upx;
  border-radius: 20upx;
  position: absolute;
  top:-80upx;
}
.topic-info .topic-info-t>view{
  font-size: 32upx;
  position: relative;
  padding:5upx 20upx;
  margin-left:80px
}
.topic-info>view{
  margin-bottom:15upx;
}
.topic-info .topic-info-m{
  color: #CDCDCD;
}
.topic-info .topic-info-b{
  color: #A3A3A3;
} 
</style>
