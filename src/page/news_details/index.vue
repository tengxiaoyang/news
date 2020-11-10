<template>
  <div class="main">
    <div class="header">
      <img src="https://p1.pstatp.com/medium/321c80005b6d5a51b0a8d">
      <span>今日头条</span>
      <div class="button">打开</div>
    </div>
    <div class="news">
      <span class="title">{{news_title}}</span>
      <div class="writer">
        <img class="left" :src="news_writer_icon" :alt="news_writer_icon_alt">
        <div class="middle">
          <span class="name">{{news_writer_name}}</span>
          <span class="info">{{news_writer_info}}</span>
        </div>
        <div class="right">关注</div>
      </div>
      <span class="content">{{news_content}}</span>
      <img class="photo" :src="news_photo" :alt="news_photo_alt">
    </div>
    <div class="related_suggestion"></div>
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
      news_content: "国家主席习近平11月10日在上海合作组织成员国元首理事会第二十次会议上发表重要讲话。",
      news_photo: "https://p3.pstatp.com/large/pgc-image/e7a638a1bc274bf5ac0eeea1e47c298a",
      news_photo_alt: "国家主席习近平在上海合作组织成员国元首理事会第二十次会议上发表重要讲话"
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
  .news {
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
}
</style>
