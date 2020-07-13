<template>
  <view>
    <template v-if="list.length>0 ">
      <block v-for="(item,index) in list" :key="index">
        <index-list :item="item" :index="index"></index-list>
      </block>
      <load-more :loadtext="loadtext"></load-more>
    </template>
    <template v-else-if="issearch && list.length<1">
      <!--无内容时展示信息-->
      <no-thing></no-thing>
    </template>
  </view>
</template>

<script>
  import indexList from "@/components/my/index-list/index-list.vue"
  import noThing from "@/components/my/no-thing/no-thing.vue"
  import loadMore from "@/components/my/load-more/load-more.vue"
  export default {
    components: {
      indexList,
      noThing,
      loadMore
    },
    data() {
      return {
        issearch: false,
        loadtext: "上拉加载更多",
        list: [],
        searchtext:'',
      }
    },
    //监听原生标题按钮事件
    onNavigationBarButtonTap(e) {
      if (e.index == 0) {
        uni.navigateBack({
          delta: 1
        });
      }
    },
    //页面搜索项改变事件
    onNavigationBarSearchInputChanged(e) {
      this.searchtext = e.text
      // if (e.text) {
        // this.issearch = true;
        // this.searchtext = e.text;
        // this.getdata(e.text);
      //   this.getdata();
      // }
    },
    //监听搜索按钮提交事件
    onNavigationBarSearchInputConfirmed(e) {
      if (e.text) {
        this.getdata();
      }
    },
    //上拉触底事件
    onReachBottom() {
      this.loadMore();
    },
    //下拉刷新
    onPullDownRefresh() {
      this.getdata();
      uni.stopPullDownRefresh();
    },
    methods: {
      loadMore() {
        let _that = this;
        if (this.loadtext != "上拉加载更多") {
          return;
        }
        this.loadtext = "加载中...";
        setTimeout(function() {
          let obj = {
            userpic: "../../static/demo/userpic/12.jpg",
            username: "wo是黄蓉",
            isguanzhu: false,
            title: "我是标题",
            type: "video",
            titlepic: "../../static/demo/datapic/11.jpg",
            infonum: {
              index: 0,
              dingnum: 11,
              cainum: 11,
            },

            comment: 10,
            share: 10
          }

          _that.loadtext = "上拉加载更多";
          _that.list.push(obj);
        }, 1000)
      },
      getdata() {
        // this.searchtext
        uni.showLoading();
        setTimeout(() => {
          this.list = [{
              userpic: "../../static/demo/userpic/12.jpg",
              username: "wo是黄蓉",
              isguanzhu: false,
              title: "我是标题",
              type: "img",
              titlepic: "../../static/demo/datapic/11.jpg",
              infonum: {
                index: 0,
                dingnum: 11,
                cainum: 11,
              },

              comment: 10,
              share: 10
            },
            {
              userpic: "../../static/demo/userpic/12.jpg",
              username: "wo是黄蓉",
              isguanzhu: false,
              title: "我是标题",
              type: "video",
              titlepic: "../../static/demo/datapic/11.jpg",
              infonum: {
                index: 1,
                dingnum: 11,
                cainum: 11,
              },

              comment: 10,
              share: 10
            },
            {
              userpic: "../../static/demo/userpic/12.jpg",
              username: "wo是黄蓉",
              isguanzhu: false,
              title: "我是标题",
              type: "video",
              titlepic: "../../static/demo/datapic/11.jpg",
              infonum: {
                index: 1,
                dingnum: 11,
                cainum: 11,
              },

              comment: 10,
              share: 10
            }
          ];
          uni.hideLoading();
        }, 1000)
      },
    }
  }
</script>

<style>

</style>
