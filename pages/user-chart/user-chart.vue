<template>
  <view class="body">
    <scroll-view scroll-y :scroll-top="scrollTop" :scroll-with-animation="true"
    :style="{height:style.contentH+'px'}">
      <!--聊天列表-->
      <block v-for="(item,index) in list" :key="index">
        <user-chart-list :item="item" :index="index"></user-chart-list>
      </block>
    </scroll-view>
    <!--输入框-->
    <user-chart-buttom @submit="submit"></user-chart-buttom>
  </view>
</template>

<script>
  import UserChartButtom from '@/components/my/user-chart/user-chart-bottom.vue'
  import UserChartList from '@/components/my/user-chart/user-chart-list.vue'
  import time from '@/common/time.js'
  export default {
    components: {
      UserChartButtom,
      UserChartList
    },
    data() {
      return {
        text: "",
        scrollTop:0,
        style:{
          contentH:0
        },
        list: [{
            isme: false,
            userpic: '../../static/topicpic/1.jpeg',
            type: "text",
            data: '哈哈哈',
            time: '1554970014'
          },
          {
            isme: true,
            userpic: '../../static/topicpic/2.jpeg',
            type: "img",
            data: '../../static/demo/3.jpg',
            time: '1555146414'
          }
        ]
      }
    },
    onLoad() {
      this.getData();
      this.initdata();
    },
    methods: {
      initdata(){
        try{
          const res = uni.getSystemInfoSync();
          console.log(res)
          this.style.contentH = res.windowHeight - uni.upx2px(120);
        }catch(e){
          
        }
      },
      submit(data) {
        let now = new Date().getTime();
        let obj =  {
            'isme': true,
            "userpic": '../../static/topicpic/2.jpeg',
            "type": "text",
            "data": data,
            "time": now,
            "gstime":time.gettime.getChatTime(now,this.list[this.list.length-1].time)
          }
          this.list.push(obj);
      },
      getData() {
        let arr = [{
            isme: false,
            userpic: '../../static/topicpic/1.jpeg',
            type: "text",
            data: '哈哈哈',
            time: '1555146412'
          },
          {
            isme: true,
            userpic: '../../static/topicpic/2.jpeg',
            type: "img",
            data: '../../static/demo/3.jpg',
            time: '1555146414'
          }
        ];
        for(let i = 0;i<arr.length;i++){
           arr[i].gstime = time.gettime.getChatTime(arr[i].time,i>0?arr[i-1].time:0)
        }
        this.list = arr;
      },
    }
  }
</script>

<style>
  .body {
    padding: 0 20upx;
  }

  
</style>
