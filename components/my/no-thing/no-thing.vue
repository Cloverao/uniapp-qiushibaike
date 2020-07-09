<template>
	<view class="nothing" animated bounceIn>
	    <image src="../../../static/common/nothing.png" mode="widthFix"></image>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
  .nothing{
        display: flex;
        justify-content: center;
        align-items: center;
        background: #FFFFFF;
        position: absolute;
        top: 0;
        left:0;
        bottom:0;
        right:0;
    }
    .nothing image{
        width:50%;
    }
</style>
