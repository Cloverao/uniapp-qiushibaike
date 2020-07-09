<template>
  <view class="content">
    <!-- <view class="icon icon-guanwangfangwen iconfont"></view>
		<uni-list>
		    <uni-list-item title="标题文字" :show-arrow="false"></uni-list-item>
		    <uni-list-item title="标题文字"></uni-list-item>
		    <uni-list-item title="标题文字" :show-badge="true" badge-text="12"></uni-list-item>
		    <uni-list-item title="禁用状态" :disabled="true" :show-badge="true" badge-text="12"></uni-list-item>
		</uni-list> -->

    <block>
      <swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap"></swiper-tab-head>
    </block>
    <view class="uni-tab-bar">
      <swiper class="swipper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
        <swiper-item v-for="(item,index) in newsList" :key="index">
          <!-- {{item.list.length}} -->
          <template v-if="item.list.length > 0">
            <scroll-view scroll-y class="list" @scrolltolower="loadmore1(index)">
              <!--图文列表-->
              <block v-for="(subitem,subindex) in item.list" :key="subindex">
               <index-list :item="subitem" :index="subindex"></index-list>
              </block>
              <!--上拉加载-->
              <!-- <view class="load-more">{{item.loadtext}}</view> -->
 <!--             {{item.loadtext}} -->
              <load-more :loadtext="item.loadtext"></load-more>
            </scroll-view>
          </template>
          <template v-else>
            <!--无内容时展示信息-->
            <no-thing></no-thing>
          </template>
        </swiper-item>
      </swiper>
    </view>
<!--    	<block v-for="(item,index) in list" :key="index">
			<index-list :item="item" :index="index"></index-list>
		</block> -->
  </view>
</template>

<script>
  // import uniList from "@/components/uni-list/uni-list.vue"
  // import uniListItem from "@/components/uni-list-item/uni-list-item.vue"
  import indexList from "@/components/my/index-list/index-list.vue"
  import swiperTabHead from "@/components/my/swiper-tab-head/swiper-tab-head.vue"
  import loadMore from "@/components/my/load-more/load-more.vue"
  import noThing from "@/components/my/no-thing/no-thing.vue"
  export default {
    components: {
      // uniList,
      // uniListItem
      indexList,
      swiperTabHead,
      loadMore,
      noThing
    },
    data() {
      return {
        swiperheight: 500,
        tabIndex: 0,
        tabBars: [{
            name: "关注",
            id: "guanzhu"
          },
          {
            name: "推荐",
            id: "tuijian"
          },
          {
            name: "体育",
            id: "tiyu"
          },
          {
            name: "热点",
            id: "redian"
          },
          {
            name: "财经",
            id: "caijing"
          },
          {
            name: "娱乐",
            id: "yule"
          }
        ],
        list: [{
            userpic: "../../../static/demo/userpic/12.jpg",
            username: "wo是黄蓉",
            isguanzhu: false,
            title: "我是标题",
            type: "img",
            titlepic: "../../../static/demo/datapic/11.jpg",
            infonum: {
              index: 0,
              dingnum: 11,
              cainum: 11,
            },

            comment: 10,
            share: 10
          },
          {
            userpic: "../../../static/demo/userpic/12.jpg",
            username: "wo是黄蓉",
            isguanzhu: false,
            title: "我是标题",
            type: "video",
            titlepic: "../../../static/demo/datapic/11.jpg",
            infonum: {
              index: 1,
              dingnum: 11,
              cainum: 11,
            },

            comment: 10,
            share: 10
          },
          {
            userpic: "../../../static/demo/userpic/12.jpg",
            username: "wo是黄蓉",
            isguanzhu: false,
            title: "我是标题",
            type: "video",
            titlepic: "../../../static/demo/datapic/11.jpg",
            infonum: {
              index: 1,
              dingnum: 11,
              cainum: 11,
            },

            comment: 10,
            share: 10
          }
        ],
        newsList: [{
          loadtext: "上拉加载更多",
          list: [{
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
          },{
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
          }]
        }, {
          loadtext: "上拉加载更多",
          list: []
        }, {
          loadtext: "上拉加载更多",
          list: []
        }, {
          loadtext: "上拉加载更多",
          list: []
        }, {
          loadtext: "上拉加载更多",
          list: []
        }, {
          loadtext: "上拉加载更多",
          list: []
        }],
      }
    },
    onNavigationBarSearchInputClicked() {
      //配置pages中disabled=true才会生效
      uni.navigateTo({
        url: '../search/search'
      });
    },
    onNavigationBarSearchInputChanged() {
      // console.log("打开搜索页1")
    },
    //监听原生标题按钮事件
    onNavigationBarButtonTap(e) {
      if (e.index == 1) {
        uni.navigateTo({
          url: '../add-input/add-input'
        });
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
      tabtap(index) {
        this.tabIndex = index
      },
      tabChange(e) {
        this.tabIndex = e.detail.current
      },
      loadmore1(index) {
        let _that = this;
        if (this.newsList[index].loadtext != "上拉加载更多") {
          return;
        }
        this.newsList[index].loadtext = "加载中...";
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

          _that.newsList[index].loadtext = "上拉加载更多";
          _that.newsList[index].list.push(obj);
        }, 1000)
        // this.newsList[index].loadtext = "上拉加载更多";
        // this.newsList[index].loadtext = "没有更多操作了";
      },
    }
  }
</script>

<style>
  .uni-swiper-tab {
    border-bottom: 1px solid #EEEEEE;
  }

  .nothing {
    display: flex;
    justify-content: center;
    align-items: center;
    background: #FFFFFF;
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
  }

  .nothing image {
    width: 50%;
  }
</style>
