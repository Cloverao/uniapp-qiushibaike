<template>
  <view class="body">
    <!--操作栏菜单-->
    <paper-left-popup :show="show" @hide="hidepopup" @addfriend="addfriend" @clear="clear"
    ></paper-left-popup>
    <scroll-view scroll-y :style="{height:swiperheight+'px'}" class="list" @scrolltolower="loadmore1(index)">
      <block v-for="(item,index) in  paperList.list " :key="index">
        <paper-list :item="item" :index="index"></paper-list>
      </block>
      <load-more :loadtext="paperList.loadtext"></load-more>
    </scroll-view>
  </view>
</template>

<script>
  import uniBadge from '@/components/uni-badge/uni-badge.vue';
  import paperList from '@/components/my/paper/paper-list.vue';
  import loadMore from "@/components/my/load-more/load-more.vue"
  import paperLeftPopup from "@/components/my/paper/paper-left-popup.vue"
  export default {
    components: {
      uniBadge,
      paperList,
      loadMore,
      paperLeftPopup
    },
    data() {
      return {
        show: false,
        swiperheight: 600,
        menuLeft: [{
            title: "加糗友",
            iconfont: 'icon iconfont icon-sousuo"'
          },
          {
            title: "清除未读",
            iconfont: 'icon iconfont icon-qingchu"'
          }
        ],
        paperList: {
          loadtext: "上拉加载更多",
          list: [{
              userpic: "../../static/topicpic/12.jpeg",
              username: '昵称',
              time: '13:48',
              data: '内容1',
              noreadnum: 0,
            },
            {
              userpic: "../../static/topicpic/13.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容2',
              noreadnum: 3,
            },
            {
              userpic: "../../static/topicpic/14.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容3',
              noreadnum: 10,
            }, {
              userpic: "../../static/topicpic/12.jpeg",
              username: '昵称',
              time: '13:48',
              data: '内容1',
              noreadnum: 0,
            },
            {
              userpic: "../../static/topicpic/13.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容2',
              noreadnum: 3,
            },
            {
              userpic: "../../static/topicpic/14.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容3',
              noreadnum: 10,
            }, {
              userpic: "../../static/topicpic/12.jpeg",
              username: '昵称',
              time: '13:48',
              data: '内容1',
              noreadnum: 0,
            },
            {
              userpic: "../../static/topicpic/13.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容2',
              noreadnum: 3,
            },
            {
              userpic: "../../static/topicpic/14.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容3',
              noreadnum: 10,
            }, {
              userpic: "../../static/topicpic/12.jpeg",
              username: '昵称',
              time: '13:48',
              data: '内容1',
              noreadnum: 0,
            },
            {
              userpic: "../../static/topicpic/13.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容2',
              noreadnum: 3,
            },
            {
              userpic: "../../static/topicpic/14.jpeg",
              username: '昵称',
              time: '14:48',
              data: '内容3',
              noreadnum: 10,
            }
          ]
        }
      }
    },
    //监听原生标题按钮事件
    onNavigationBarButtonTap(e) {
      switch(e.index) {
           case 0:
              this.toMyFriends();
              break;
           case 1:
              this.showpopup()
              break;
           default:
              默认代码块
      } 
    
    },
    //监听下拉刷新事件
    onPullDownRefresh() {
      this.refreshData();
    },
    //监听下拉刷新事件
    onReachBottom() {
      this.loadmore1();
    },
    onLoad() {
      uni.getSystemInfo({
        success: function(res) {
          // console.log(res.model);
          // console.log(res.pixelRatio);
          // console.log(res.windowWidth);
          let height = res.windowHeight - uni.upx2px(100);
          this.swiperheight = height
          // console.log(res.language);
          // console.log(res.version);
          // console.log(res.platform);
        }
      });
    },
    methods: {
      toMyFriends(){
        uni.navigateTo({
          url:"../user-list/user-list"
        })
      },
      refreshData() {
        let arr = [{
            userpic: "../../static/topicpic/15.jpeg",
            username: '昵称',
            time: '13:48',
            data: '内容1',
            noreadnum: 0,
          },
          {
            userpic: "../../static/topicpic/16.jpeg",
            username: '昵称',
            time: '14:48',
            data: '内容2',
            noreadnum: 3,
          },
          {
            userpic: "../../static/topicpic/12.jpeg",
            username: '昵称',
            time: '14:48',
            data: '内容3',
            noreadnum: 10,
          }, {
            userpic: "../../static/topicpic/11.jpeg",
            username: '昵称',
            time: '13:48',
            data: '内容1',
            noreadnum: 0,
          },
          {
            userpic: "../../static/topicpic/14.jpeg",
            username: '昵称',
            time: '14:48',
            data: '内容2',
            noreadnum: 3,
          },
          {
            userpic: "../../static/topicpic/14.jpeg",
            username: '昵称',
            time: '14:48',
            data: '内容3',
            noreadnum: 10,
          }
        ];
        let that = this;
        setTimeout(function() {
          that.paperList.list = arr;
          uni.stopPullDownRefresh();
        }, 1000)
      },
      loadmore1() {
        let _that = this;
        if (this.paperList.loadtext != "上拉加载更多") {
          return;
        }
        this.paperList.loadtext = "加载中...";
        setTimeout(function() {
          let obj = {
            userpic: "../../static/topicpic/14.jpeg",
            username: '昵称',
            time: '14:48',
            data: '内容3',
            noreadnum: 10,
          }

          _that.paperList.loadtext = "上拉加载更多";
          _that.paperList.list.push(obj);
        }, 1000)
      },
      addfriend() {
        console.log("加糗友");
        this.hidepopup();
        this.$emit("addfriend")
      },
      clear() {
        console.log("清除未读");
        this.hidepopup();
      },
      hidepopup() {
        this.show = false
      },
      showpopup() {
        this.show = true
      },
    }
  }
</script>

<style>
  .body {
    padding: 0 20upx;
  }
</style>
