<template>
  <div class="main">
    <div class="header">
      <div class="back" v-on:click="route_to('/')"></div>
      频道管理
    </div> 
    <div class="middle">
      <div class="title">点击删除以下频道</div>
      <div class="content">
        <div class="option" v-for="(item, index) of option_delete" :key="index" v-bind:style="item.option_name_style">{{item.option_name}}</div>
      </div>
    </div>
    <div class="bottom">
      <div class="title">点击添加以下频道</div>
      <div class="content">
        <div class="option" v-for="(item, index) of option_add" :key="index">{{item.option_name}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'more',
  data() {
    return {
      option_delete: [
        {
          option_name: "推荐",
          option_name_style: "background: #f0f0f0;"
        },
        {
          option_name: "热点"
        },
        {
          option_name: "社会"
        },
        {
          option_name: "娱乐"
        },
        {
          option_name: "科技"
        },
        {
          option_name: "汽车"
        },
        {
          option_name: "体育"
        },
        {
          option_name: "财经"
        },
        {
          option_name: "军事"
        },
        {
          option_name: "国际"
        },
        {
          option_name: "时尚"
        },
        {
          option_name: "游戏"
        },
      ],
      option_add: [
        {
          option_name: "旅游"
        },
        {
          option_name: "历史"
        },
        {
          option_name: "探索"
        },
        {
          option_name: "美食"
        },
        {
          option_name: "育儿"
        },
        {
          option_name: "养生"
        },
        {
          option_name: "故事"
        },
        {
          option_name: "美文"
        },
      ]
    }
  },
  methods: {
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
  },
  
}

</script>

<style lang="less" scoped>
body {
  background: #f8f8f8;
}
.main {
  .header {
    width: 100%;
    height: 50px;
    background: #d43d3d;
    color: #fff;
    font-size: 20px;
    font-weight: 800;
    text-align: center;
    line-height: 50px;
    .back {
      background: url(https://s3a.pstatp.com/growth/wap_misc/image/header_back_86a065fc5fe6605cd32e26fe9a2c9f37.png);
      background-size: 100%;
      width: 24px;
      height: 24px;
      float: left;
      margin: 13px 12px;
      position: absolute;
      top: 0;
      left: 0;
    }
  }
  .middle, .bottom {
    .title {
      font-size: 12px;
      color: #666;
      font-weight: 400;
      padding: 4px 8px;
    }
    .content {
      width: 100%;
      display: grid;
      grid-template-columns: 1fr 1fr 1fr 1fr;
      margin: 0 0 10px 0;
      padding: 0 2px;
      .option {
        font-size: 16px;
        color: #131313;
        font-weight: 400;
        border: 1px solid #ccc;
        height: 34px;
        text-align: center;
        line-height: 32px;
        margin: 7px 6px;
      }
    }
  }
}

</style>
