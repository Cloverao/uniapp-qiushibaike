<template>

  <!--上拉加载-->
  <view class="load-more">{{loadtext}}</view>

</template>

<script>
  export default {
    props: {
      loadtext: String
    },
    data() {
      return {

      }
    },
    mounted() {
    },
    methods: {

    }
  }
</script>

<style>
  .load-more {
    text-align: center;
    color: #aaaaaa;
    padding: 15upx;
  }
</style>
