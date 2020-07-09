<template>
  <view>
    <!--话题信息-->
    <topic-info :topicInfo="topicInfo"></topic-info>
    <!--tab切换-->
    <swiper-tab-head :tabIndex="tabIndex" :tabBars="tabBars" @tabtap="tabtap" scrollItemStyle="width:50%" scrollStyle="border-bottom:0;"></swiper-tab-head>
    <!--列表-->
    <view class="topic-detail-list uni-tab-bar">
      <block v-for="(item,index) in tabList" :key="index">
        <template v-if="tabIndex==index">
          <scroll-view scroll-y :style="{height:swiperheight+'px'}" class="list" @scrolltolower="loadmore1(index)">
            <block v-for="(subItem,subIndex) in item.list" :key="subIndex">
              <common-list :item="subItem" :index="subIndex"></common-list>
            </block>
            <load-more :loadtext="item.loadtext"></load-more>
          </scroll-view>
        </template>
      </block>
    </view>
  </view>
</template>

<script>
  import topicInfo from "@/components/my/topic/topic-info.vue"
  import swiperTabHead from "@/components/my/swiper-tab-head/swiper-tab-head.vue"
  import commonList from "@/components/my/common-list/common-list.vue"
  import loadMore from "@/components/my/load-more/load-more.vue"
  export default {
    components: {
      topicInfo,
      swiperTabHead,
      commonList,
      loadMore
    },
    data() {
      return {
        swiperheight: 400,
        topicInfo: {
          titlepic: '../../static/topicpic/13.jpeg',
          title: '忆回忆，敬往事',
          desc: '面试官：加入你在电梯里遇到马云你会跟他说什么？90后女孩回答当场被录用',
          totalnum: '987',
          todaynum: '641',
        },
        tabIndex: 0,
        tabBars: [{
            name: "默认",
            id: "moren"
          },
          {
            name: "最新",
            id: "zuixin"
          }
        ],
        tabList: [{
          loadtext: "上拉加载更多",
          list: [
            //分享 图文
            {
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
            //文本
            {
              userpic: "../../static/demo/userpic/2.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: false,
              share: {
                title: "分享内容",
                titlepic: ""
              },
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            //视频
            {
              userpic: "../../static/demo/userpic/3.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: {
                looknum: "20w",
                long: "2:43"
              },
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            {
              userpic: "../../static/demo/userpic/4.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 15,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/3.jpg",
              video: false,
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            {
              userpic: "../../static/demo/userpic/5.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 21,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "",
              video: false,
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
          ]
        }, {
          loadtext: "上拉加载更多",
          list: [
            //分享 图文
            {
              userpic: "../../static/demo/userpic/1.jpg",
              username: "三文鱼xiaoje",
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
            //文本
            {
              userpic: "../../static/demo/userpic/2.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: false,
              share: {
                title: "分享内容",
                titlepic: ""
              },
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            //视频
            {
              userpic: "../../static/demo/userpic/3.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: {
                looknum: "20w",
                long: "2:43"
              },
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            {
              userpic: "../../static/demo/userpic/4.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 15,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/3.jpg",
              video: false,
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            {
              userpic: "../../static/demo/userpic/5.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 21,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "",
              video: false,
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
          ]
        }]
      }
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
    //监听下拉刷新事件
    onPullDownRefresh() {
     this.refreshData();
    },
    //到底加载更多
    onReachBottom(){
      this.loadmore1()
    },
    methods: {
      refreshData(){
        let that = this;
        setTimeout(function() {
          let arr = [{
              userpic: "../../static/demo/userpic/1.jpg",
              username: "追风少女",
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
            //文本
            {
              userpic: "../../static/demo/userpic/2.jpg",
              username: "穿的的",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: false,
              share: {
                title: "分享内容",
                titlepic: ""
              },
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            //视频
            {
              userpic: "../../static/demo/userpic/3.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 20,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/2.jpg",
              video: {
                looknum: "20w",
                long: "2:43"
              },
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            },
            {
              userpic: "../../static/demo/userpic/4.jpg",
              username: "三文鱼小姐",
              sex: 1, //0:男，1女
              age: 15,
              isguanzhu: false,
              title: "论王者荣耀",
              titlepic: "../../static/demo/datapic/3.jpg",
              video: false,
              share: false,
              path: "深圳 龙岗",
              sharenum: 20,
              commentnum: 30,
              goodnum: 20
            }]
          that.tabList[that.tabIndex].list = arr ;
          uni.stopPullDownRefresh();
        }, 1000);
      },
      tabtap(index) {
        this.tabIndex = index
      },
      loadmore1(index) {
        let _that = this;
        if (this.tabList[index].loadtext != "上拉加载更多") {
          return;
        }
        this.tabList[index].loadtext = "加载中...";
        setTimeout(function() {
          let obj = {
            userpic: "../../static/demo/userpic/5.jpg",
            username: "三文鱼小姐",
            sex: 1, //0:男，1女
            age: 21,
            isguanzhu: false,
            title: "论王者荣耀",
            titlepic: "",
            video: false,
            share: false,
            path: "深圳 龙岗",
            sharenum: 20,
            commentnum: 30,
            goodnum: 20
          }

          _that.tabList[index].loadtext = "上拉加载更多";
          _that.tabList[index].list.push(obj);
        }, 1000)
      },
    }
  }
</script>

<style>

</style>
