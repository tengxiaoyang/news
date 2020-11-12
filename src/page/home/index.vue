<template>
<div class="home_container">
  <div class="header">
    <div class="top">
      <div class="left">
        <div class="message" @click="get_message_window()">
        </div>
      </div>
      <div class="middle">
        <div class="icon"></div>
        <div class="refresh"></div>
      </div>
      <div class="right">
        <div class="search" @click="route_to('search')"></div>
      </div>
    </div>
    <div class="bottom">
      <div class="option_outside">
        <a class="recommended_option" @click="get_news(0)">推荐</a>
        <!-- <a class="option">视频</a> -->
        <a class="option" @click="get_news(1)">热点</a>
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
      <a class="plus_sign"  @click="route_to('more')">
        <div class="horizontal_line"></div>
        <div class="vertical_line"></div>
      </a>
    </div>
  </div>
  <div class="content">
    <div class="news" v-for="(item, index) of news_content" :key="index" @click="route_to('news_details')">
      <!-- <div class="news_normal" v-if="item.show_news_normal"> -->
      <div class="news_normal">
        <div class="news_top">
          <div class="news_left">
            <div class="news_title">{{item.name}}</div>
            <div class="news_information">
              <span class="news-sticky_content" v-if="item.show_sticky_content">{{item.sticky_content}}</span>
              <div class="news-writer">{{item.author}}</div>
              <div class="news-number_of_comments">评论 {{item.comment}}</div>
              <div class="news-release_time" v-if="item.show_release_time">{{item.release_time}}小时前</div>
            </div>
          </div>
          <div class="news_right">
            <div class="news-photo_outside">
              <img class="news-photo" v-bind:src="item.img1">
              <div class="play_button" v-if="item.show_play_button"></div>
            </div>
          </div>
        </div>
        <div class="news_bottom"></div>
      </div>
      <div class="news_app_promotion" v-if="item.show_news_app_promotion">
        <div class="top">
          <img class="promotion_photo" :src="item.promotion_photo">
        </div>
        <div class="bottom">
          <div class="promotion_letter">{{item.promotion_letter}}</div>
          <div class="promotion_name">{{item.promotion_name}}</div>
        </div>
      </div>
      <div class="news_advertisement" v-if="item.show_news_advertisement">
        <div class="top">
          <div class="ad_title">{{item.ad_title}}</div>
        </div>
        <div class="middle">
          <img class="ad_photo" :src="item.ad_photo">
        </div>
        <div class="bottom">
          <span class="ad_text">{{item.ad_text}}</span>
          <div class="ad_product">{{item.ad_product}}</div>
          <div class="ad-number_of_comments">评论 {{item.ad_number_of_comments}}</div>
          <div class="ad-release_time">{{item.ad_release_time}}小时前</div>
        </div>
      </div>
    </div>
  </div>
  <div class="bottom_banner_under"></div>
  <div class="bottom_banner">
    <div class="left"></div>
    <div class="middle">今日头条</div>
    <div class="right" @click="route_to('download')">打开</div>
  </div>
  <div class="message_window_outside" v-if="show_message_window">
    <div class="message_window">
      <div class="top">
        <div class="left"></div>
        <div class="middle">
          <div class="middle_inside">
            <div class="photo"></div>
            <span class="title">已加载好您感兴趣的头条</span>
          </div>
        </div>
        <div class="right">
          <div class="cross" @click="get_message_window()"></div>
        </div>
      </div>
      <div class="bottom">
        <div class="button">立即打开</div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import HttpClient from '../../config/ajax.js';

export default {
  name: 'home',
  data() {
    return {
      show_message_window: false,
      now_type: 0,
      news_content: [
        // {
        //   show_news_normal: true,
        //   news_title: "习近平对川藏铁路开工建设作出重要指示强调 发扬“两路”精神和青藏铁路精神 高质量推进工程建设 李克强作出批示",
        //   show_sticky_content: true,
        //   sticky_content: "置顶",
        //   writer: "新华网客户端",
        //   number_of_comments: "1378",
        //   show_release_time: true,
        //   release_time: "2",
        //   photo: "",
        //   show_play_button: false,
        //   show_news_app_promotion: false,
        //   show_news_advertisement: false
        // },
        // {
        //   show_news_normal: true,
        //   news_title: "焦点访谈：“十四五”时期，中国将着重办好哪些事？",
        //   show_sticky_content: true,
        //   sticky_content: "置顶",
        //   writer: "央视网新闻",
        //   number_of_comments: "608",
        //   show_release_time: true,
        //   release_time: "2",
        //   photo: "",
        //   show_play_button: false,
        //   show_news_app_promotion: false,
        //   show_news_advertisement: false
        // },
        // {
        //   show_news_normal: true,
        //   news_title: "7首歌，一起走过71年",
        //   show_sticky_content: false,
        //   sticky_content: "置顶",
        //   writer: "人民网",
        //   number_of_comments: "400",
        //   show_release_time: false,
        //   release_time: "2",
        //   photo: "http://p1-tt-ipv6.byteimg.com/img/tos-cn-i-0004/14a069d7bc264501b7c8ff2157b6633a~tplv-tt-cs0:640:360.jpg",
        //   show_play_button: true,
        //   show_news_app_promotion: false,
        //   show_news_advertisement: false
        // },
        // {
        //   show_news_normal: false,
        //   news_title: "7首歌，一起走过71年",
        //   show_sticky_content: false,
        //   sticky_content: "置顶",
        //   writer: "人民网",
        //   number_of_comments: "400",
        //   show_release_time: false,
        //   release_time: "2",
        //   photo: "http://p1-tt-ipv6.byteimg.com/img/tos-cn-i-0004/14a069d7bc264501b7c8ff2157b6633a~tplv-tt-cs0:640:360.jpg",
        //   show_play_button: true,
        //   show_news_app_promotion: true,
        //   promotion_photo: "http://s2.pstatp.com/site/promotion/landing_page/img/午夜_6584dfd45e8f505ae91d52209df7065c.jpg",
        //   promotion_letter: "APP",
        //   promotion_name: "今日头条",
        //   show_news_advertisement: false
        // },        
        // {
        //   show_news_normal: false,
        //   news_title: "7首歌，一起走过71年",
        //   show_sticky_content: false,
        //   sticky_content: "置顶",
        //   writer: "人民网",
        //   number_of_comments: "400",
        //   show_release_time: false,
        //   release_time: "2",
        //   photo: "http://p1-tt-ipv6.byteimg.com/img/tos-cn-i-0004/14a069d7bc264501b7c8ff2157b6633a~tplv-tt-cs0:640:360.jpg",
        //   show_play_button: true,
        //   show_news_app_promotion: false,
        //   show_news_advertisement: true,
        //   ad_title: "长安UNI-T，限时十重礼，等你来享！",
        //   ad_photo: "http://sf3-ttcdn-tos.pstatp.com/img/web.business.image/202011065d0d0a679d2bc2104ee5ae35~640x0.image?from=ad",
        //   ad_text: "广告",
        //   ad_product: "懂车帝优选",
        //   ad_number_of_comments: "0",
        //   ad_release_time: "7"
        // },
        
      ]

    }
  },
  computed: {
    // num() {
    //   return this.$store.state.num;
    // }
  },
  created() {
  
  },
  mounted() {
    console.log(this.now_type),
    HttpClient.getList({  
      params: { type:  this.now_type },  
      callback: (res) => {
        console.log(res.data.data), 
        this.news_content = res.data.data
      } 
    });  
  },
  methods: {
    // addNum() {
    //   let r = Math.floor(Math.random() * 10);
    //   console.log(r);
    //   this.$store.commit('ADD_NUM', r)
    // },
    get_message_window() {
      this.show_message_window = !this.show_message_window
    },
    route_to(e) {
      this.$router.push({path: e})
    },
    get_news(e) {
      console.log(e)
      HttpClient.getList({  
        params: { type:  e },  
        callback: (res) => {
          console.log(res.data.data), 
          this.news_content = res.data.data,
          this.now_type = e
          console.log(this.now_type)
        } 
      });

    },

  }
}
</script>

<style lang="less" scoped>
.header {
  width: 100%;
  height: 85px;
  position: fixed;
  z-index: 1;
}
.header .top {
  width: 100%;
  height: 44px;
  display: flex;
  background: #d43d3d;
}
.header .top .left {
  width: 88px;
  height: 42px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .left .message {
  width: 25px;
  height: 22px;
  background: url(//s3.pstatp.com/growth/mobile_list/image/feed_ic_message_normal@3x_f2ea949f.png) no-repeat;
  background-size: contain;
}
.header .top .right {
  width: 88px;
  height: 42px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .right .search {
  width: 25px;
  height: 22px;
  background: url(//s3.pstatp.com/growth/mobile_list/image/feed_ic_search_normal@3x_0f198e56.png) no-repeat center;
  background-size: contain;
}
.header .top .middle {
  width: 100%;
  height: 43px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .top .middle .icon {   
  width: 109px;
  height: 34px;
  background: url(//s3b.pstatp.com/growth/mobile_list/image/wap_logo@3x_581de69e.png) no-repeat right center;
  background-size: 83px;
}
.header .top .middle .refresh {    
  width: 22px;
  height: 34px;
  background: url(//s3a.pstatp.com/growth/mobile_list/image/titlebar_refresh_small@3x_96fb31e4.png) no-repeat center center;
  background-size: 15px;
}
.header .bottom {
  display: flex;
  width: 100%;
  height: 40px;
  overflow: hidden;
  background: #f4f5f6;
}
.header .bottom .plus_sign {
  width: 38px;
  height: 38px;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
}
.header .bottom .plus_sign .horizontal_line {    
  width: 16px;
  height: 2px;
  background: #f85959;
}
.header .bottom .plus_sign .vertical_line {
  position: absolute;
  width: 2px;
  height: 16px;
  background: #f85959;
}
.header .bottom .option_outside {
  width: 100%;
  height: 51px;
  overflow: hidden;
  overflow-x: scroll;
  white-space: nowrap;
  position: relative;
}
.header .bottom .recommended_option {
  display: inline-block;
  width: 64px;
  height: 38px;
  margin: 0px -4px;
  text-align: center;
  line-height: 38px;
  font-size: 18px;
  color: #f85959;
}
.header .bottom .option {
  display: inline-block;
  width: 64px;
  height: 38px;
  margin: 0px -4px;
  text-align: center;
  line-height: 38px;
  font-size: 18px;
  color: #000;
}
.content {
  padding: 9px 16px 0 16px;
  position: relative;
  top: 78px;
}

.news {
  padding: 10px 0px;
  .news_normal {
    .news_top {
      display: flex;
      .news_left {
        flex: 1;
        .news_title {
          font-size: 17px;
          color: #000;
          font-weight: 400;
        }
        .news_information {
          display: -ms-flexbox;
          display: flex;
          -ms-flex-align: center;
          height: 28px;
          span {
            padding: 1px 3.5px;
            font-size: 12px;
            border: 1px solid rgba(248, 89, 89, 0.5);
            color: #f85959;
            height: 17px;
          }
          div {
            padding: 1px 2.5px;
            font-size: 12px;
            height: 17px;
            font-weight: 400;
            color: #999;
          }
        }
      }
      .news_right {
        max-width: 27vw;
        .news-photo_outside {
          width: 100%;
          display: flex;
          justify-content: center;
          align-items: center;
          .news-photo {
            width: 100%;
          }
          .play_button {
            background: url(https://s3.pstatp.com/growth/mobile_list/image/playicon_video@3x_dcf536ff.png) no-repeat center center;
            width: 7%;
            height: 7%;
            background-size: 100%;
            display: block;
            position: absolute;
          }
        }
      }
    }
    .news_bottom {
      border-bottom: 1px solid #F8F8F8;
    }
    
  }
  .news_app_promotion {
    .top {
      .promotion_photo {
        width: 91vw;
        padding: 20px 0 0 0;
      }
    }
    .bottom {
      font-size: 17px;
      color: #000;
      font-weight: 400;
      display: flex;
      height: 28px;
      border-bottom: 1px solid #F8F8F8;
      align-items: center;
      .promotion_letter {
        padding: 1px 3.5px;
        font-size: 12px;
        border: 1px solid rgba(248, 89, 89, 0.5);
        color: #f85959;
        height: 17px;
      }
      .promotion_name {
        padding: 1px 2.5px;
        font-size: 12px;
        height: 17px;
      }
    }
  }
  .news_advertisement {
    .top {
      .ad_title {
        font-size: 17px;
        color: #000;
        font-weight: 400;
      }
    }
    .middle {
      .ad_photo {
        width: 91vw;
      }
    }
    .bottom {
      font-size: 17px;
      color: #000;
      font-weight: 400;
      display: flex;
      height: 28px;
      border-bottom: 1px solid #F8F8F8;
      align-items: center;
      .ad_text {
        padding: 1px 3.5px;
        font-size: 12px;
        border: 1px solid rgba(42, 144, 215, 0.5);
        color: #2a90d7;
        height: 17px;
      }
      div {
        padding: 1px 2.5px;
        font-size: 12px;
        height: 17px;
      }
    }
  }
}
.bottom_banner_under {
  width: 100%;
  height: 50px;
  background: #fff;
  position: relative;
  top: 78px;
}
.bottom_banner {
  position: fixed;
  bottom: -2px;
  width: 100%;
  height: 50px;
  display: flex;
  align-items: center;
  background: #fff;
  .left {
    width: 41px;
    height: 38px;
    background: url(https://s3.bytecdn.cn/growth/fe_sdk/image/banner_toutiao_icon_bce0b302.png);
    background-size: 100%;
      margin: 0 8px 0 12px;
  }
  .middle {
    flex: 1;
    height: 20px;
    font-size: 15px;
    font-weight: 400;
  }
  .right {
    width: 64px;
    height: 24px;
    background: #ff5050;
    border-radius: 20px;
    margin: 0 12px 0 0;
    font-size: 14px;
    color: #fff;
    text-align: center;
    line-height: 24px;
  }
}
.message_window_outside {
  display: flex;
  position: fixed;
  top: 0;
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  background: rgba(0,0,0,.5);
  z-index: 1;
}
.message_window {
  position: relative;
  width: 75%;
  background: #fff;
  border-radius: 8px;
  padding: 0 0 7px 0;
  .top {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 177px;
    .left,.right {
      width: 33px;
      height: 176px;
      .cross {
        width: 33px;
        height: 27px;
        background: url(https://s3.pstatp.com/growth/mobile_list/image/popup_banner_close_e6f62910.png) no-repeat center;
        background-size: 53%;
      }
    }
    .middle {
      height: 160px;
      width: 212px;
      display: flex;
      justify-content: center;
      .middle_inside {
        height: 158px;
        width: 164px;
        .photo {
          width: 162px;
          height: 122px;
          background: url(https://s3a.pstatp.com/growth/mobile_list/image/popup_banner_6006ac97.png);
          background-size: 100%;
        }
        .title {
          position: absolute;
          left: 36px;
          display: block;
          height: 36px;
          width: 75%;
          font-size: 17px;
          text-align: center;
          line-height: 36px;
          color: #A5A5A5;
        }
      }
    }
  }
  .bottom {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 44px;
    .button {
      width: 82%;
      height: 96%;
      text-align: center;
      line-height: 200%;
      font-size: 21px;
      color: #fff;
      background: #ff6762;
    }
  }
}

</style>
