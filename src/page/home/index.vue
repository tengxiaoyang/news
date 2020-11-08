<template>
<div class="home_container">
  <div class="header">
    <div class="top">
      <div class="left">
        <div class="message"></div>
      </div>
      <div class="middle">
        <div class="icon"></div>
        <div class="refresh"></div>
      </div>
      <div class="right">
        <div class="search"></div>
      </div>
    </div>
    <div class="bottom">
      <div class="option_outside">
        <a class="recommended_option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
        <a class="option"></a>
      </div>
      <a class="plus_sign">
        <div class="horizontal_line"></div>
        <div class="vertical_line"></div>
      </a>
    </div>
  </div>
  <div class="content">
    <div class="news" v-for="(item,index) of news_content" :key="item.id">{{item}}/{{index}}
      <div class="news_left">
        <div class="news_title"></div>
        <div class="news_writer"></div>
      </div>
      <div class="news_right"></div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      news_content: [
        {},
        123, 456111, 111, 45
        ]

    }
  },
  computed: {
    num() {
      return this.$store.state.num;
    }
  },
  methods: {
    addNum() {
      let r = Math.floor(Math.random() * 10);
      console.log(r);
      this.$store.commit('ADD_NUM', r)
    },

  }
}
</script>

<style lang="less" scoped>
.header {
  width: 100%;
  height: 85px;
  border: 1px solid #000;
}
.header .top {
  width: 100%;
  height: 44px;
  border: 1px solid #000;
  display: flex;
  background: #d43d3d;
}
.header .top .left {
  width: 88px;
  height: 42px;
  border: 1px solid #000;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .left .message {
  width: 25px;
  height: 22px;
  border: 1px solid #000;
  background: url(//s3.pstatp.com/growth/mobile_list/image/feed_ic_message_normal@3x_f2ea949f.png) no-repeat;
  background-size: contain;
}
.header .top .right {
  width: 88px;
  height: 42px;
  border: 1px solid #000;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .right .search {
  width: 25px;
  height: 22px;
  border: 1px solid #000;
  background: url(//s3.pstatp.com/growth/mobile_list/image/feed_ic_search_normal@3x_0f198e56.png) no-repeat center;
  background-size: contain;
}
.header .top .middle {
  width: 100%;
  height: 43px;
  border: 1px solid #000;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .middle .icon {   
  width: 109px;
  height: 34px;
  border: 1px solid #000;
  background: url(//s3b.pstatp.com/growth/mobile_list/image/wap_logo@3x_581de69e.png) no-repeat right center;
  background-size: 83px;
}
.header .top .middle .refresh {    
  width: 22px;
  height: 34px;
  border: 1px solid #000;
  background: url(//s3a.pstatp.com/growth/mobile_list/image/titlebar_refresh_small@3x_96fb31e4.png) no-repeat center center;
  background-size: 15px;
}
.header .bottom {
  display: flex;
  width: 100%;
  height: 40px;
  border: 1px solid #000;
  overflow: hidden;
}
.header .bottom .plus_sign {
  width: 38px;
  height: 38px;
  border: 1px solid #000;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .bottom .plus_sign .horizontal_line {    
  width: 16px;
  border: 1px solid #000;
}
.header .bottom .plus_sign .vertical_line {
  position: absolute;
  height: 16px;
  border: 1px solid #000;
}
.header .bottom .option_outside {
  width: 100%;
  height: 51px;
  border: 1px solid #000;
  overflow: hidden;
  overflow-x: scroll;
  white-space: nowrap;
  position: relative;
  bottom: 2px;
}
.header .bottom .recommended_option {
  display: inline-block;
  width: 64px;
  height: 38px;
  border: 1px solid #000;    
  margin: 0px -4px;
}
.header .bottom .option {
  display: inline-block;
  width: 64px;
  height: 38px;
  border: 1px solid #000;    
  margin: 0px -4px;
}
</style>
