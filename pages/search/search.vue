<template>
	<view>
		search
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
        //监听原生标题按钮事件
        onNavigationBarButtonTap	(e){
            console.log(e.index)
            if(e.index == 0) {
                uni.navigateBack({
                    delta: 1
                });
            }
        },
        //页面搜索项改变事件
        onNavigationBarSearchInputChanged(e){
            console.log(e.text)
        },
        //监听搜索按钮提交事件
        onNavigationBarSearchInputConfirmed(e){
            console.log(e.text)
        },
		methods: {
			
		}
	}
</script>

<style>

</style>
