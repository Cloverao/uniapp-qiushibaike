<template>
  <view>
    <news-nav-bar :tabIndex="tabIndex" :tabBars="tabBars" @change-tab="changeTab"></news-nav-bar>
    <view class="uni-tab-bar">
      <swiper class="swipper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
        <swiper-item>
          <scroll-view scroll-y class="list" @scrolltolower="loadmore1(index)">
            <block v-for="(item,index) in guanzhu.list" :key="index">
              <common-list :item="item" :index="index"></common-list>
            </block>
            <load-more :loadtext="guanzhu.loadtext"></load-more>
          </scroll-view>

        </swiper-item>
        <swiper-item>
          <scroll-view scroll-y class="list">
            <!--搜索框-->
            <!-- <uni-search-bar @confirm="search" @input="input" @cancel="cancel"  placeholder="搜索内容"/> -->
            <view class="search-input">
              <input class="uni-input" placeholder-class="icon iconfont icon-sousuo toppic-search" placeholder="搜索内容" />
            </view>
            <!--轮播图-->
            <swiper class="toppic-swipper" circular :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval"
              :duration="duration">
              <block v-for="(item,index) in toppic.swiper">
                <swiper-item >
                  <image :src="item.src" mode="widthFix" lazy-load></image>
                </swiper-item>
              </block>
            </swiper>
            <!--热门分类-->
            <toppic-nav :nav="toppic.nav"></toppic-nav>
            <!--最近更新-->
            
            <view class="topic-new">
              <view>最近更新</view>
              <block v-for="(item,index) in toppic.list">
                <toppic-list :item="item" :index="index"></toppic-list>
              </block>
              
              
            </view>
          </scroll-view>
        </swiper-item>
      </swiper>
    </view>
  </view>
</template>

<script>
  import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'
  import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
  import commonList from "@/components/my/common-list/common-list.vue"
  import newsNavBar from "@/components/my/news/news-nav-bar.vue"
  import toppicNav from "@/components/my/news/topic-nav.vue"  
  import toppicList from "@/components/my/news/topic-list.vue"  
  import loadMore from "@/components/my/load-more/load-more.vue"
  export default {
    components: {
      uniSearchBar,
      uniNavBar,
      commonList,
      newsNavBar,
      loadMore,
      toppicNav,
      toppicList
    },
    data() {
      return {
        indicatorDots: true,
        autoplay: false,
        interval: 2000,
        duration: 500,
        toppic:{
          swiper:[
            {src:"../../static/demo/banner1.jpg"},
            {src:"../../static/demo/banner2.jpg"},
            {src:"../../static/demo/banner3.jpg"}
          ],
          nav:[
            {name:"最新"},
            {name:'游戏'},
            {name:'情感'},
            {name:'打卡'},
            {name:'故事'},
            {name:'喜爱'}
          ],
          list:[
            {
              titlepic:"../../static/topicpic/1.jpeg",
              title:"标题",
              desc:"内容",
              totalnum:50,
              todaynum:10
            },
            {
              titlepic:"../../static/topicpic/1.jpeg",
              title:"标题",
              desc:"内容",
              totalnum:50,
              todaynum:10
            },
            {
              titlepic:"../../static/topicpic/1.jpeg",
              title:"标题",
              desc:"内容",
              totalnum:50,
              todaynum:10
            },
            {
              titlepic:"../../static/topicpic/1.jpeg",
              title:"标题",
              desc:"内容",
              totalnum:50,
              todaynum:10
            },
            {
              titlepic:"../../static/topicpic/1.jpeg",
              title:"标题",
              desc:"内容",
              totalnum:50,
              todaynum:10
            }
          ]
        },
        
        swiperheight: 600,
        tabIndex: 0,
        tabBars: [{
            "title": "关注",
            "id": '1'
          },
          {
            'title': '话题',
            'id': '2'
          }
        ],
        guanzhu: {
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
        },

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
    methods: {
      changeTab(index) {
        this.tabIndex = index
      },
      tabChange(e) {
        this.tabIndex = e.detail.current
      },
      loadmore1(index) {
        let _that = this;
        if (this.guanzhu.loadtext != "上拉加载更多") {
          return;
        }
        this.guanzhu.loadtext = "加载中...";
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

          _that.guanzhu.loadtext = "上拉加载更多";
          _that.guanzhu.list.push(obj);
        }, 1000)
      },
      // search(){},
      // input(){},
      // cancel(){},
    }
  }
</script>

<style>
  .search-input {
    padding: 10upx 0;
  }

  .search-input>input {
    background-color: #F4F4F4;
    border-radius: 10upx;
  }

  .toppic-search {
    display: flex;
    justify-content: center;
    font-size: 25upx;
  }

  .toppic-swipper {
      /* height: 300rpx; */
      padding:0 20upx 20upx 20upx;
    }
    .toppic-swipper image{
      width: 100%;
      border-radius: 10upx;
    }
    
    
    
</style>
