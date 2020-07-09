<template>
	
	<view class="index-list animated bounceInRight fast">
		<view class="index-list1 u_flex">
			<view class="u_flex">
				<image :src="item.userpic" mode="widthFix" lazy-load></image>
				{{item.username}}
			</view>
			
			<view class="u_flex" v-show="!isguanzhu" @tap="guanzhu">
				<view class="icon iconfont icon-zengjia"></view>关注
			</view>
		</view>
		<view class="index-list2" @tap="opendetail">
			{{item.title}}
		</view>
		<view class="index-list3 u_flex">
			<image :src="item.titlepic" mode="widthFix"></image>
			<view class="index-list-play icon iconfont icon-bofang" v-show="item.type != 'img'"></view>
			<view class="index-list-playinfo" v-show="item.type != 'img'">
				20w次播放 2:43
			</view>
		</view>
		<view class="index-list4 u_flex">
			<view class="u_flex" >		
					<view class="icon iconfont icon-icon_xiaolian-mian" :class="{'active':infonum.index == 1}" @tap="caozuo('ding')"></view>
					<view :class="{'active':infonum.index == 1}">{{infonum.dingnum}}</view>
					<view class="icon iconfont icon-kulian" :class="{'active':infonum.index ==2}" @tap="caozuo('cai')"></view>
					<view :class="{'active':infonum.index == 2}">{{infonum.cainum}}</view>
			</view>
			<view class="u_flex">
					<view class="icon iconfont icon-pinglun1"></view><view>{{item.comment}}</view>
					<view class="icon iconfont icon-zhuanfa"></view><view>{{item.share}}</view>
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
				isguanzhu:this.item.isguanzhu,
        infonum:this.item.infonum
			}
		},
    mounted(){
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
            caozuo(type){
                 switch(type){
                     case "ding" :
                         if(this.infonum.index == 1){return}
                         this.infonum.dingnum++;
                         if(this.infonum.index == 2){
                             this.infonum.cainum--;
                         }
                         this.infonum.index = 1
                         break;
                     case "cai":
                         if(this.infonum.index == 2){return}
                         this.infonum.cainum++;
                         if(this.infonum.index == 1){
                             this.infonum.dingnum--;
                        }
                         this.infonum.index = 2
                         break;
                 }
            },
            opendetail(){
                
            },
		}
	}
</script>

<style>
.u_flex{
		display: flex;
	}
	.index-list{
		padding:20upx;
		border-bottom:1upx solid #EEEEEE;
	}
	.index-list1{
		
		justify-content: space-between;
		align-items: center;
	}
		
	.index-list2{
		padding-top:15upx;
	}
	.index-list3{
		padding-top:15upx;
		position: relative;
		justify-content: center;
		align-items: center;
	}
	.index-list-play{
		position: absolute;
		color:#FFFFFF;
		font-size: 110upx;
	}
	.index-list-playinfo{
		position: absolute;
		background-color: rgba(51,51,51,0.72);
		color: #FFFFFF;
		bottom: 8upx;
		right:8upx;
		border-radius: 40upx;
		font-size: 25upx;
		padding:0 10upx;
	}
	.index-list4{
		padding:15px 0;
		
		justify-content: space-between;
		align-items: center;
	}
	.index-list1>view{

		align-items: center;
		color: #999999;
	}
	.index-list1>view:first-child image{
		width:90upx;
		height:90upx;
		border-radius: 90upx;
		margin-right: 10upx;
	}
	.index-list1>view:last-child{
	
		align-items: center;
		background-color: #EEEEEE;
		border-radius: 5upx;
		padding:0px 5px;
		color: #333333;
	}
	.index-list3>image{
		width:100%;
		border-radius: 20upx;
	}
	.index-list4>view{
		justify-content: space-between;
		color: #999999;
	}
	.index-list4>view>view{
		margin:0 3px;
	}
	.index-list4>view>view.active{
		color: #09BB07;
	}
</style>
