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
        <div class="update_time"></div>
      </div>
      <div class="content">
        <div class="content_item" v-for="(item, index) of hot_search" :key="index">
          <div class="left" v-if="!item.show_red_mark"></div>
          <div class="left_red" v-if="item.show_red_mark"></div>
          <div class="middle"></div>
          <div class="right">
            <div class="hot" v-if="item.show_hot"></div>
            <div class="burst" v-if="item.show_burst"></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'search',
  data() {
    return {
      name: 'helloworld vue'
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
    border: 1px solid #000;
    .empty_area {
      border: 1px solid #000;
      height: 18vh;
    }
    .icon {
      border: 1px solid #000;
      width: 100%;
      height: 11vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
    .search_bar {
      width: 100%;
      height: 11vh;
      border: 1px solid #000;
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
          padding: 12px 11px;
          flex: 1;
        }
        .zoom {
          padding: 12px 11px;
        }
      }
    }
  }
  .bottom {
    margin: 31px 0 0 0;
    .title {
      border: 1px solid #000;
      width: 100%;
      height: 33px;
      display: flex;
      align-items: center;
      img {
        width: 22px;
        height: 22px;
        margin: 0 0 0 12px;
      }
      .name {
        font-size: 17px;
        font-weight: 400;
      }
    }
  }
}

</style>
