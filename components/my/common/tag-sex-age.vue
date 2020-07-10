<template>
	<view class="icon iconfont icon-nan common-list-info-age"
	 :class="[sex == 0?'icon-nan' : 'icon-nv']"
	> {{age}} </view>
</template>

<script>
	export default {
    props:{
      sex:Number,
      age:Number
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
 .common-list-info-age {
    border-radius: 18upx;
    font-size: 18upx;
    padding: 0 10upx;
    
    background-color: #007AFF;
    color: #FFFFFF;
  }
  .icon-nv{
    background-color: #FF688D !important;
  }
</style>
