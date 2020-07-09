<template>
	<view class="paper-list c_flex animated bounceInRight fast">
	  <image :src="item.userpic" mode="widthFix" lazy-load></image>
	  <view>
	    <view class="c_flex c_flex_j_sb">
	      <view>
	        {{item.username}}
	      </view>
	      <view>
	       {{item.time}}
	      </view>
	    </view>
	    <view class="c_flex c_flex_j_sb">
	      <view>
	        {{item.data}}
	      </view>
	      <view>
	        <template v-if="item.noreadnum > 0">
            <uni-badge class="uni-badge-left-margin" :text="item.noreadnum" type="error" size="small" />
          </template>
	      </view>
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

<style>
  .paper-list {
    border-bottom: 1upx solid #EEEEEE;
    padding: 20upx 0;
  }

  .paper-list>view {
    flex: 1;
  }

  .paper-list>image {
    width: 100upx;
    border-radius: 100%;
    flex-shrink: 0;
    margin-right: 20upx;
  }

  .paper-list>view:last-child>view:first-child>view:last-child {
    color: #CDCDCD;
  }

  .paper-list>view:last-child>view:last-child {
    color: #999999;
  }

  .paper-list>view:last-child {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
</style>
