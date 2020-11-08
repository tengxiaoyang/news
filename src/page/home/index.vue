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
        <a class="recommended_option">推荐</a>
        <a class="option">视频</a>
        <a class="option">热点</a>
        <a class="option">社会</a>
        <a class="option">娱乐</a>
        <a class="option">军事</a>
        <a class="option">科技</a>
        <a class="option">汽车</a>
        <a class="option">房产</a>
        <a class="option">家居</a>
        <a class="option">体育</a>
        <a class="option">财经</a>
      </div>
      <a class="plus_sign">
        <div class="horizontal_line"></div>
        <div class="vertical_line"></div>
      </a>
    </div>
  </div>
  <div class="content">
    <div class="news" v-for="(item, index) of news_content" :key="index">
      <div class="news_left">
        <div class="news_title">{{item.news_title}}</div>
        <div class="news_information">
          <span class="news-sticky_content">{{item.sticky_content}}</span>
          <div class="news-writer">{{item.writer}}</div>
          <div class="news-number_of_comments">评论 {{item.number_of_comments}}</div>
          <div class="news-release_time">{{item.release_time}}小时前</div>
        </div>
      </div>
      <div class="news_right">
        <div class="news-photo_outside">
          <img class="news-photo" v-bind:src="item.photo">
        </div>
      </div>
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
        {
          news_title: "习近平对川藏铁路开工建设作出重要指示强调 发扬“两路”精神和青藏铁路精神 高质量推进工程建设 李克强作出批示",
          sticky_content: "置顶",
          writer: "新华网客户端",
          number_of_comments: "1378",
          release_time: "2"
        },
        {
          news_title: "焦点访谈：“十四五”时期，中国将着重办好哪些事？",
          sticky_content: "置顶",
          writer: "央视网新闻",
          number_of_comments: "608",
          release_time: "2"
        },
        {
          news_title: "7首歌，一起走过71年",
          sticky_content: "置顶",
          writer: "人民网",
          number_of_comments: "400",
          release_time: "2",
          photo: "http://p1-tt-ipv6.byteimg.com/img/tos-cn-i-0004/14a069d7bc264501b7c8ff2157b6633a~tplv-tt-cs0:640:360.jpg"
        },
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
  background: #f4f5f6;
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
  height: 2px;
  // border: 1px solid #f85959;
  background: #f85959;
}
.header .bottom .plus_sign .vertical_line {
  position: absolute;
  width: 2px;
  height: 16px;
  // border: 1px solid #f85959;
  background: #f85959;
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
  text-align: center;
  line-height: 38px;
  font-size: 18px;
  color: #000;
}
.header .bottom .option {
  display: inline-block;
  width: 64px;
  height: 38px;
  border: 1px solid #000;
  margin: 0px -4px;
  text-align: center;
  line-height: 38px;
  font-size: 18px;
  color: #000;
}
.content {
  padding: 15px 16px;
}
.news {
  border: 1px solid #000;
  display: flex;
  .news_left {
    border: 1px solid #000;
    flex: 1;
    .news_title {
      font-size: 19px;
      border: 1px solid #000;
    }
    .news_information {
      font-size: 19px;
      border: 1px solid #000;
      display: -ms-flexbox;
      display: flex;
      -ms-flex-align: center;
      height: 28px;
      border-bottom: 1px solid #F8F8F8;
      span {
        padding: 1px 1.5px;
        font-size: 12px;
        border: 1px solid  rgba(248, 89, 89, 0.5);
        color: #f85959;
        height: 20px;
      }
      div {
        padding: 1px 1.5px;
        font-size: 12px;
        border: 1px solid #000;
        height: 20px;
      }
    }
  }
  .news_right {
    max-width: 14vh;
    .news-photo_outside {
    width: 100%;
      .news-photo {
        width: 100%;
      }
    }
  }
}
</style>
