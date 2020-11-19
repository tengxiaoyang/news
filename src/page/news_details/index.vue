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
    <div class="popular_discussion">
      <div class="top">
        <span class="title">热门讨论</span>
        <span class="see_more">打开今日头条看更多</span>
      </div>
      <div class="discussion" v-for="(item, index) of discussion_content" :key="index" @click="route_to('discussion_details')">
        <div class="writer">
          <img class="left" :src="item.news_writer_icon" :alt="item.news_writer_icon_alt">
          <img class="v_sign" :src="item.news_writer_v_sign" alt="" v-if="item.show_v_sign">
          <div class="middle">
            <span class="name">{{item.news_writer_name}}</span>
            <span class="info">{{item.news_writer_info}}</span>
          </div>
          <div class="right">关注</div>
        </div>
        <div class="content">{{item.discussion_content}}</div>
        <div class="bottom">
          <span class="transmit"></span>
          转发
          <span class="comment"></span>
          {{item.comment_num}}
          <span class="like"></span>
          {{item.like_num}}
        </div>
      </div>
    </div>
    <div class="top_comments">
      <div class="top">
        <span class="title">热门评论</span>
        <span class="see_more">打开今日头条看更多</span>
      </div>
      <div class="comment" v-for="(item, index) of comment_content" :key="index" @click="route_to('comment_details')">
        <div class="writer">
          <img class="writer_icon" :src="item.writer_icon" :alt="item.writer_icon_alt">
          <span class="writer_name">{{item.writer_name}}</span>
          <span class="like_num">{{item.like_num}}</span>
          <div class="thumbs_up"></div>
        </div>
        <div class="content">
          <span class="comment_text">{{item.comment_text}}</span>
          <div class="bottom">
            <span class="reply">
              回复
              <div class="arrow"></div>
            </span>
            <span class="update_time">{{item.update_time}}</span>
          </div>
        </div>
      </div>
    </div>
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
      discussion_content: [
        {
          news_writer_icon: "https://p3.pstatp.com/thumb/46db000246c0cdd9fab8",
          news_writer_icon_alt: "林起",
          news_writer_v_sign: "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYCAMAAADXqc3KAAAAS1BMVEVMaXH70UH////71En73nb73Gv611r/5Z784oj9447///v+8cL71lL95Y/72V///PH833v84oX+9M/83Gz/+uf966v96aP+9tj+77lrciyUAAAACnRSTlMA////1+r5MqqEgXHQlQAAAMFJREFUeNp1ktsSgyAQQ024KXhttfb/v7RdEbpTx/PCDFkSJtCchNZ5Y7xrQ6MJFhWrpM5AYbqy3+KP9pzHhe7wN7hgJMcCkUICMEcBsN8DMpBIjhBmxkEsQk7uq7DxdeY7CA/mjTGuOdI1HsJArrImzjjwTR7oI/kEnnwgY0Q4vTZgj2MVPIrXhEXEYuVQveZ16ovgalGJnDiougIyC8kdlSCV5LTjXgWrSkx8qxJV7csvGZ1+KKOT75/2/jPcfp8P2DQGvLjl4yEAAAAASUVORK5CYII=",
          show_v_sign: true,
          news_writer_name: "林起",
          news_writer_info: "财经作家 代表作《雪球投资》",
          discussion_content: "中国恒大：终止与深深房的重组计划，恒大重组深深房A以失败告终。这对深房伤害太大了，好比一个深闺的少女，待字闺中等大郎，这左等右等一年年过去了，从少女等到少妇，等来的是“我无法娶你”的噩耗，犹如晴天霹雳，现在少妇要走出闺房了，还有人要吗？",
          comment_num: "16",
          like_num: "14"
        },
      ],
      comment_content: [
        {
          writer_icon: "https://sf6-ttcdn-tos.pstatp.com/img/pgc-image/26e6fef9e1cd4890a4edf831ba0d260c~120x256.image",
          writer_name: "阔老总祝愿大家都幸福",
          like_num: "268",
          comment_text: "祝大会圆满成功！祝福祖国繁荣昌盛！为习主席点赞！",
          update_time: "15小时前",
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
    // this.$store.commit('REMBER_TIME');
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
  .related_suggestion, .popular_discussion {
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
.discussion {
  .writer {
    display: flex;
    align-items: center;
    position: relative;
    .left {
      width: 36px;
      height: 36px;
      margin: 0 0 0 21px;
      border-radius: 50px;
    }
    .v_sign {
      position: absolute;
      width: 13px;
      height: 13px;
      left: 44px;
      top: 21px;
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
    font-size: 16px;
    line-height: 25px;
    color: #232323;
    font-weight: 400;
    margin: 7px 21px 8px;
    overflow: hidden;
    text-overflow: ellipsis;
    display: -webkit-box;
    -webkit-line-clamp: 3;
    /* autoprefixer: off */
    -webkit-box-orient: vertical;
  }
  .bottom {
    font-size: 14px;
    color: #707070;
    font-weight: 400;
    margin: 0 0px 0 20px;
    .transmit {
      display: inline-block;
      background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABIBAMAAACnw650AAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAqUExURUxpcW9vb29vb29vb3BwcG9vb29vb3BwcHBwcHBwcHBwcG9vb29vb3BwcJK24j8AAAANdFJOUwAggEDvEDDP35u3UGiV7DUrAAAA0ElEQVRIx2NgGAWDBLBVJBBWxHXXjRhFVwgbxdhLjFESNDWK7ZASGtC8i24Ud+1dLOBKAIqiuXexAgNkNZzY1VxHMejs3VsbBTGBAIqitXcVCPqW9e4twkHCfPcOMYoujzxFbIpEKBJBSQU4FNmipIJRRQysvQWEFTEwMhChiGEEKjpLhCLW3iuEDQq/exOFn6SECTR97zqixIov9kJsA0rewa7GG9WJWIvVpgB0N17BKA5FMXxbS0zxH05MTUJdoxYQY9QEwopYJwWMNk8oAwB+DtuvfZvXYgAAAABJRU5ErkJggg==) no-repeat 50%;
      background-size: contain;
      background-position: 0 0;
      width: 51px;
      text-align: right;
      width: 24px;
      height: 24px;
      vertical-align: middle;
    }
    .comment {
      display: inline-block;
      background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABIBAMAAACnw650AAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAtUExURUxpcW9vb29vb29vb29vb29vb3BwcHBwcG9vb29vb3BwcG9vb29vb29vb3BwcBYAnDUAAAAOdFJOUwCAYCBAodvvMBC/kHBQ/3rbNQAAAPdJREFUeNrt0rFqwlAUxvEPolCxgym4OOUJJKA4C+6FvoCLUykExMUpZHOVDg6OPoAP4FDq2qlbt6KBxiLyPYOJXDgRr1ccXOT+tnP5c5Z7YFnX+aLODHlT6lWQ80G9HYRDvrinatxAPHIHnS4jGcpcQeeXngzFM9Gzje4s+iEPeqZorqL1+UjOODZF7+pwPfstdxWV+Q+dOtsyFJh0GpmxemgcNEOOIYLjY2tR+UPOiMonUk5ApQchz/HRoq2PvMLSTVW5iYBSwL6befKhM+cAmGSpwYSJny4awsQJ+Fokv2HUYhIyhtlDSNLDBSMyxiXO4i2CdTt7CTMhEicaP/8AAAAASUVORK5CYII=) no-repeat 50%;
      background-size: contain;
      background-position: 0 0;
      width: 51px;
      text-align: right;
      width: 24px;
      height: 24px;
      vertical-align: middle;
      margin: 0 0 0 37px;
    }
    .like {display: inline-block;
      background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAEgAAABICAMAAABiM0N1AAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAzUExURUxpcXBwcHBwcG9vb3BwcG9vb29vb3BwcG9vb29vb29vb3BwcG9vb29vb29vb3BwcHBwcOaH+V8AAAAQdFJOUwDPrxDfIFu/gKCQ70BwMH9vr9/lAAABYUlEQVR42u2W3a6EIBCDQUH+XOX9n3bRyaa65wiu9dLeKAn5Ai3MoB49asl2brgFZHLOxvKcIa963bCge0hzYXQrbOScXhhWhcWnnuCshFi+rnw9s6BPYjblrAlQV0ByiOKyRSp6g9+Bin7AJj2zoPAZyD8TPUCRiD5s8/Nc9KLxutlhd8F8GU2XOCOiV3K0Exc99tldjt7th8lspBtls7ciRC/S+a+MPaTMJm8UVA1UKSx2h9nfUeu+lY8PlnAgVZEUFnNob4pepAGqnbPD2mObs6DuaIpD3nUQ/Nd3gHrkyoFGXEUO9JJWx4DgdU+D4DUPQjngQBO85kADvOZAEV5zIIcry4GSzCZA8NqTILwpOBC8nkgQ2hwHgtccCP0ykiA8KUgQnhQ0CIWfB2mZS4DgdaiB9EnQDK+JBikc09df52HTsv3/CikX+aqD5xUa7+qzio0u7E+hTBzVo0ePftAbflAqQpNfW3YAAAAASUVORK5CYII=) no-repeat 50%;
      background-size: contain;
      background-position: 0 0;
      width: 51px;
      text-align: right;
      width: 24px;
      height: 24px;
      vertical-align: middle;
      margin: 0 0 0 37px;
    }
  }
}
.top_comments {
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
  .comment {
    margin: 0 18px 0;
    .writer {
      display: flex;
      align-items: center;
      .writer_icon {
        width: 30px;
        height: 30px;
        border-radius: 30px;
      }
      .writer_name {
        color: #222;
        font-size: 14px;
        font-weight: 800;
        margin: 0 0 0 11px;
        flex: 1;
      }
      .like_num {
        color: #222;
        font-size: 14px;
        font-weight: 400;
      }
      .thumbs_up {
        background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAMAAAC7IEhfAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAzUExURUxpcQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOV/WOUAAAAQdFJOUwDvvxAgP99ggJ/PUHCPkK/5nOnBAAAAtElEQVR42u3TwQ7CIBCE4YUuu2xtdd7/aU2xCUY0w8GDB/8Lh37JJDTIb6VzzBMQC3eKlA3GpWMTCVQKV6jIkoy5gvzgDAb8ODKDChMOG/B22meoRzuytGDaGtmKlp2fDGfxYityRO5/RKN1G66+oog4fJi6os7AfvUUyopJCJuDF8QcDJQ5mEw47MscBgqBfZnDvsxhoHDYlzncECO8ugfCn9uRdHx870pFhnSrQ77Iv293B+jXCylQ6FAKAAAAAElFTkSuQmCC) no-repeat 50%;
        background-size: contain;
        width: 20px;
        height: 20px;
        margin: 0 0 0 4px;
      }
    }
    .content {
      margin: 10px 0 7px 41px;
      .comment_text {
        display: block;
        font-size: 16px;
        color: #222;
        font-weight: 400;
        line-height: 28px;
      }
      .bottom {
        .reply {
          color: #222;
          font-size: 12px;
          font-weight: 400;
          background: #f2f2f2;
          display: inline-block;
          width: 55px;
          height: 24px;
          line-height: 24px;
          border-radius: 24px;
          padding: 0 7px 0;
          .arrow {
            display: inline-block;
            background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABgAAAAYBAMAAAASWSDLAAAABGdBTUEAALGPC/xhBQAAAAFzUkdCAK7OHOkAAAAbUExURUxpcR8fHyIiIiEhIR8fHyEhISEhIR8fHyIiIhjTciMAAAAIdFJOUwAg388wkKAQTv9WEQAAADVJREFUGNNjYCATuAogcTIUkThCTUhSjBrkSRkgcxSwK0MxAFmC3QJJohjZ4AhkK90EGMgGAKJvB8cZh0MoAAAAAElFTkSuQmCC) no-repeat 50%;
            background-size: contain;
            width: 12px;
            height: 12px;
            position: relative;
            top: 1px;
          }
        }
        .update_time {
          color: #999;
          font-size: 12px;
          font-weight: 400;
          margin: 0 0 0 6px;
        }
      }
    }
  }
}
</style>
