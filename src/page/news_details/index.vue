<template>
  <div class="main">
    <div class="header">
      <img src="https://p1.pstatp.com/medium/321c80005b6d5a51b0a8d">
      <span>今日头条</span>
      <div class="button">打开</div>
    </div>
    <div class="news_detail">
      <span class="title">{{news_title}}</span>
      <div class="writer">
        <img class="left" :src="news_writer_icon" :alt="news_writer_icon_alt">
        <div class="middle">
          <span class="name">{{news_writer_name}}</span>
          <span class="info">{{news_writer_info}}</span>
        </div>
        <div class="right">关注</div>
      </div>
      <span class="content">{{news_details}}</span>
      <img class="photo" :src="news_photo" :alt="news_photo_alt">
    </div>
    <div class="related_suggestion">
      <div class="top">
        <span class="title">相关推荐</span>
        <span class="see_more">打开今日头条看更多</span>
      </div>
      <div class="news" v-for="(item, index) of news_content" :key="index" @click="route_to('news_details')">
        <div class="news_normal" v-if="item.show_news_normal">
          <div class="news_top">
            <div class="news_left">
              <div class="news_title">{{item.news_title}}</div>
              <div class="news_information">
                <span class="news-sticky_content" v-if="item.show_sticky_content">{{item.sticky_content}}</span>
                <div class="news-writer">{{item.writer}}</div>
                <div class="news-number_of_comments">评论 {{item.number_of_comments}}</div>
                <div class="news-release_time" v-if="item.show_release_time">{{item.release_time}}小时前</div>
              </div>
            </div>
            <div class="news_right">
              <div class="news-photo_outside">
                <img class="news-photo" v-bind:src="item.photo">
                <div class="play_button" v-if="item.show_play_button"></div>
              </div>
            </div>
          </div>
          <div class="news_bottom"></div>
        </div>
      </div>

    </div>
    <div class="popular_discussion"></div>
    <div class="top_comments"></div>
  </div>
</template>

<script>
export default {
  name: 'news_details',
  data() {
    return {
      news_title: "国家主席习近平在上海合作组织成员国元首理事会第二十次会议上发表重要讲话",
      news_writer_icon: "https://p1.pstatp.com/thumb/ffbc0000ad1e717b76a6",
      news_writer_icon_alt: "新华社",
      news_writer_name: "新华社",
      news_writer_info: "2小时前 · 新华社官方账号",
      news_details: "国家主席习近平11月10日在上海合作组织成员国元首理事会第二十次会议上发表重要讲话。",
      news_photo: "https://p3.pstatp.com/large/pgc-image/e7a638a1bc274bf5ac0eeea1e47c298a",
      news_photo_alt: "国家主席习近平在上海合作组织成员国元首理事会第二十次会议上发表重要讲话",
      news_content: [
        {
          show_news_normal: true,
          news_title: "人生没有下辈子，请珍惜当下的一切，让这一生，活得最美！",
          show_sticky_content: false,
          sticky_content: "置顶",
          writer: "力量5201314",
          number_of_comments: "8",
          show_release_time: false,
          release_time: "2",
          photo: "https://p3-tt.bytecdn.cn/large/pgc-image/42cc5d49745c44249cbffb41f00aa49a",
          show_play_button: false,
          show_news_app_promotion: false,
          show_news_advertisement: false
        },
      ],
    }
  },
  methods: {
    get_message_window() {
      this.show_message_window = !this.show_message_window
    },
    route_to(e) {
      this.$router.push({path: e})
    }
  },
  created(){
    //进入题目页面，开始计时
    this.$store.commit('REMBER_TIME');
  },
  filters: {
    capitalize: function(value) {
      return value.toUpperCase();
    }
  }
}

</script>

<style lang="less" scoped>
.main {
  .header {
    width: 100%;
    height: 50px;
    display: flex;
    align-items: center;
    img {
      width: 38px;
      height: 38px;
      margin: 0 6px 0 18px;
      border: 1px solid #eee;
      border-radius: 5px;
    }
    span {
      flex: 1;
      font-size: 14px;
      font-weight: 400;
    }
    .button {
      width: 72px;
      height: 28px;
      font-size: 14px;
      font-weight: 400;
      background: #f04142;
      color: #fff;
      text-align: center;
      line-height: 28px;
      margin: 0 19px 0 0;
      border-radius: 5px;
    }
  }
  .news_detail {
    .title {
      font-size: 24px;
      font-weight: 800;
      display: block;
      padding: 21px 21px 15px 21px;
      color: #222;
      line-height: 36px;
    }
    .writer {
      display: flex;
      align-items: center;
      .left {
        width: 36px;
        height: 36px;
        margin: 0 0 0 21px;
      }
      .right {
        width: 56px;
        height: 28px;
        border: .02rem solid #d8d8d8;
        border-radius: .18rem;
        font-size: 14px;
        font-weight: 400;
        text-align: center;
        line-height: 28px;
        margin: 0 20px 0 0;
      }
      .middle {
        flex: 1;
        margin: 0 0 0 9px;
        .name {
          display: block;
          font-size: 14px;
          color: #222;
          font-weight: 400;
        }
        .info {
          display: block;
          font-size: 12px;
          color: #bcbcbc;
          font-weight: 400;
        }
      }
    }
    .content {
      font-size: 18px;
      color: #404040;
      font-weight: 400;
      margin: 25px 22px 20px;
      display: block;
      line-height: 30px;
    }
    .photo {
      width: 90vw;
      max-width: 100%;
      max-height: 100%;
      margin: 0 5vw 0;
    }
  }
  .related_suggestion {
    .top {
      display: flex;
      align-items: center;
      margin: 40px 18px 17px 18px;
      .title {
        flex: 1;
        font-size: 17px;
        color: #222;
        font-weight: 900;
      }
      .see_more {
        font-size: 12px;
        color: #f04142;
        font-weight: 400;
      }
      .see_more::after {
        content: "";
        display: inline-block;
        width: 12px;
        height: 12px;
        background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACEAAAAkCAMAAAAw96PuAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAzUExURUxpcfA/QO8/P/BBQe8/P/BBQvBBQe8/P/BAQfBBQfBBQfBAQe8/P/BAQe8/Qu8/QvBBQnJqC2oAAAAQdFJOUwBgEM8w76Agf9+/kECvUHA6kNbiAAAAcklEQVR42tXSRw7DMAxEUUoiVdzy73/a3GBoIM7Cs34gwWL/iI8ETMK1OCF0lbFgaeJxi7QqSQE2k/kAPRsZ9pxMTfo9UqSoDbg0WRBVEk/7bMD4aZr5COjZdU8FDvSH5F821hMgPFulBLZDMZ1y2FvzBRIPBlByP+/+AAAAAElFTkSuQmCC) no-repeat 50%;
        background-size: contain;
        position: relative;
        top: 1px;
      }
    }
  }
}

.news {
  padding: 10px 19px;
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
</style>
