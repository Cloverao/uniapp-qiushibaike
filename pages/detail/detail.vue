<template>
	<view>
    <detail-info :item="detail"></detail-info>
	</view>
</template>

<script>
  import detailInfo from "../../components/my/detail/detail-info.vue"
	export default {
    components:{
      detailInfo
    },
		data() {
			return {
				detail:{
              userpic: "../../static/demo/userpic/1.jpg",
              username: "三文鱼先生",
              sex: 0, //0:男，1女
              age: 25,
              isguanzhu: false,
              title: "论王者",
              titlepic: "",
              video: false,
              share: {
                title: "",
                titlepic: "../../static/demo/datapic/1.jpg",
              },
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
			}
		},
    onLoad(e) {
      console.log(e)
      this.initdata(JSON.parse(e.detailData));
    },
    onNavigationBarButtonTap(e) {
      if(e.index == 0){
        console.log("分享")
      }
    },
		methods: {
			initdata(obj){
        uni.setNavigationBarTitle({
          title:obj.title
        })
      },
		}
	}
</script>

<style>

</style>
