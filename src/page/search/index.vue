<template>
  <div class="main">
    <div class="top">
      <div class="empty_area"></div>
      <div class="icon">
        <img class="icon_img" src="https://sf6-ttcdn-tos.pstatp.com/obj/card-system/HeadBar/dist_browser/images/logo.545e6c99.png">
      </div>
      <div class="search_bar">
        <div class="frame">
          <span class="text">搜你想看</span>
          <div class="zoom">
            <img src="../../image/zoom.svg">
          </div>
        </div>
      </div>
    </div>
    <div class="bottom">
      <div class="title">
        <img src="https://sf6-ttcdn-tos.pstatp.com/obj/card-system/HeadBar/dist_browser/images/icon_hot.40711151.png">
        <div class="name">头条热榜</div>
        <div class="update_time">更新时间：{{update_time}}</div>
      </div>
      <div class="content">
        <div class="content_item" v-for="(item, index) of hot_search" :key="index">
          <div class="left" v-if="!item.show_red_mark">{{item.num}}</div>
          <div class="left_red" v-if="item.show_red_mark">{{item.num}}</div>
          <div class="middle">{{item.news}}</div>
          <div class="right">
            <div class="hot" v-if="item.show_hot"></div>
            <div class="burst" v-if="item.show_burst"></div>
          </div>
        </div>
      </div>
      <div class="see_more">
        <span>查看更多</span>
        <img src="https://sf6-ttcdn-tos.pstatp.com/obj/card-system/HeadBar/dist_browser/images/arrow-right-3x.85440730.png">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'search',
  data() {
    return {
      update_time: "2020/11/09 17:41",
      hot_search: 
      [
        {
          show_red_mark: true,
          num: 1,
          news: "31省份新增22例：本土1例在上海",
          show_hot: true,
          show_burst: false,
        },
        {
          show_red_mark: true,
          num: 2,
          news: "拜登团队敦促联邦批准权力交接",
          show_hot: false,
          show_burst: true,
        },
        {
          show_red_mark: true,
          num: 3,
          news: "美再制裁4名内地及香港官员",
          show_hot: false,
          show_burst: false,
        },
        {
          show_red_mark: false,
          num: 4,
          news: "且看蓬佩奥这条变色龙如何变",
          show_hot: true,
          show_burst: false,
        },
        {
          show_red_mark: false,
          num: 5,
          news: "小霸王被申请破产",
          show_hot: true,
          show_burst: false,
        },
        {
          show_red_mark: false,
          num: 6,
          news: "全球日增确诊超49万",
          show_hot: false,
          show_burst: false,
        },
        {
          show_red_mark: false,
          num: 7,
          news: "网曝辛巴卖燕窝：4元进货40元出售",
          show_hot: false,
          show_burst: false,
        },
        {
          show_red_mark: false,
          num: 8,
          news: "拜登对蔡英文“已读不回”",
          show_hot: true,
          show_burst: false,
        }
      ]
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
  width: 100%;
  height: 100%;
  background: #fff;
  .top {
    width: 100%;
    height: 40vh;
    .empty_area {
      height: 17vh;
    }
    .icon {
      width: 100%;
      height: 11vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .search_bar {
      width: 100%;
      height: 11vh;
      display: flex;
      justify-content: center;
      align-items: center;
      .frame {
        width: 90vw;
        height: 50px;
        border: 1px solid #000;
        display: flex;
        .text {
          display: block;
          font-size: 18px;
          color: #9b9b9b;
          padding: 12px 16px;
          flex: 1;
        }
        .zoom {
          padding: 12px 11px;
        }
      }
    }
  }
  .bottom {
    margin: 25px 0 0 0;
    .title {
      width: 100%;
      height: 33px;
      display: flex;
      align-items: center;
      img {
        width: 20px;
        height: 20px;
        margin: 0 5px 0 12px;
      }
      .name {
        font-size: 16px;
        font-weight: 400;
        flex: 1;
      }
      .update_time {
        font-size: 12px;
        width: 165px;
        font-weight: 400;
        color: #999;
        margin: 0 9px 0 0;
      }
    }
    .content {
      .content_item {
        display: flex;
        padding: 4px 0;
        margin: 0px 14px;
        border-bottom: 1px solid #e8e8e8;
        .left_red {
          color: rgb(240, 65, 66);
          font-size: 16px;
          font-weight: 400;
          padding: 6px 13px 6px 0;
        }
        .left {
          color: #999999;
          font-size: 16px;
          font-weight: 400;
          padding: 6px 13px 6px 0;
        }
        .middle {
          flex: 1;
          color: #000;
          font-size: 16px;
          font-weight: 400;
          padding: 6px 0px;
        }
        .right {
          .hot {
            background: url(https://p9-tt.byteimg.com/img/mosaic-legacy/2dd45000253c7757a4224~cs_noop.png);
            background-size: 100%;
            width: 16px;
            height: 16px;
            margin: 10px 0;
          }
          .burst {
            background: url(https://p1-tt.byteimg.com/img/mosaic-legacy/2dd45000253bfb6e6fc01~cs_noop.png);
            background-size: 100%;
            width: 16px;
            height: 16px;
            margin: 10px 0;
          }
        }
      }
    }
    .see_more {
      display: flex;
      justify-content: center;
      align-items: center;
      margin: 11px 0;
      span {
        font-size: 14px;
        font-weight: 400;
        text-align: center;
      }
      img {
        width: 16px;
        height: 16px;
      }
    }
  }
}

</style>
