<template>
  <view class="body">
    <!-- <uni-search-bar radius="5" placeholder="搜索糗事" clearButton="always" cancelButton="always" @confirm="search" /> -->
    <block>
      <swiper-tab-head :tabBars="tabBars" :tabIndex="tabIndex" @tabtap="tabtap" scrollItemStyle="width:33%" scrollStyle="border-bottom:0;"></swiper-tab-head>
    </block>
    <!--还有列表-->
    <view class="uni-tab-bar">
      <swiper class="swipper-box" :style="{height:swiperheight+'px'}" :current="tabIndex" @change="tabChange">
        <swiper-item v-for="(item,index) in usersList" :key="index">
          <template v-if="item.list.length > 0">
            <scroll-view scroll-y class="list" @scrolltolower="loadmore1(index)">
              <!--图文列表-->
              <block v-for="(subItem,subIndex) in item.list" :key="subIndex">
                <user-list :item="subItem" :index="subIndex"></user-list>
              </block>
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
  </view>
</template>

<script>
  // import uniSearchBar from '@/components/uni-search-bar/uni-search-bar.vue'
  import swiperTabHead from "@/components/my/swiper-tab-head/swiper-tab-head.vue"
  import userList from "@/components/my/user-list/user-list.vue"
  import loadMore from "@/components/my/load-more/load-more.vue"
  import noThing from "@/components/my/no-thing/no-thing.vue"
  export default {
    components: {
      swiperTabHead,
      userList,
      loadMore,
      noThing,
    },
    data() {
      return {
        swiperheight: 500,
        tabIndex: 0,
        tabBars: [{
            name: "互关",
            id: "heguan",
            num: 10
          },
          {
            name: "关注",
            id: "guanzhu",
            num: 10
          },
          {
            name: "粉丝",
            id: "fensi",
            num: 10
          }
        ],
        list: [{
          userpic: '../../static/topicpic/1.jpeg',
          username: 'Cloverao',
          age: 20,
          sex: 0,
          isguanzhu: false
        }, ],
        usersList: [{
          loadtext: "",
          list: [{
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }]
        }, {
          loadtext: "",
          list: [{
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }]
        }, {
          loadtext: "",
          list: [{
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }, {
            userpic: '../../static/topicpic/1.jpeg',
            username: 'Cloverao',
            age: 20,
            sex: 0,
            isguanzhu: false
          }]
        }]
      }
    },
    // 页面搜索项改变事件
    onNavigationBarSearchInputChanged(e) {},
    // 监听搜索按钮提交事件
    onNavigationBarSearchInputConfirmed(e) {
      uni.showToast({
        title: `搜索： ${e.text}`,
        icon: 'none'
      })
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
    onNavigationBarButtonTap(e) {
      if (e.index == 0) {
        uni.navigateBack({
          delta: 1
        });
      }
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
        if (this.userList[index].loadtext != "上拉加载更多") {
          return;
        }
        this.userList[index].loadtext = "加载中...";
        setTimeout(function() {
          let obj = {
            userpic: '../../static/topicpic/6.jpeg',
            username: '你好先生',
            age: 25,
            sex: 1,
            isguanzhu: true
          }
          _that.userList[index].loadtext = "上拉加载更多";
          _that.userList[index].list.push(obj);
        }, 1000)
      },
    }
  }
</script>

<style>
  .body {
    padding: 20upx;
  }
</style>
