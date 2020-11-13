<template>
  <div class="main">
    <div class="header">
      <div class="back" v-on:click="route_to('/')"></div>
      频道管理
    </div> 
    <div class="middle">
      <div class="title">点击删除以下频道</div>
      <div class="content">
        <div class="option" 
          v-for="(item, index) of option_top" 
          :key="index" 
          v-bind:style="item.option_name_style"
          @click="move_to_bottom(item.type)"
        >{{item.option_name}}</div>
      </div>
    </div>
    <div class="bottom">
      <div class="title">点击添加以下频道</div>
      <div class="content">
        <div class="option" 
          v-for="(item, index) of option_bottom" 
          :key="index"
          @click="move_to_top(item.type)"
        >{{item.option_name}}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'more',
  data() {
    return {
      option_top: [
        { 
          type: 0,
          option_name: "推荐",
          option_name_style: "background: #f0f0f0;"
        },
        {
          type: 1,
          option_name: "热点"
        },
        {
          type: 2,
          option_name: "社会"
        },
        {
          type: 3,
          option_name: "娱乐"
        },
        {
          type: 4,
          option_name: "科技"
        },
        {
          type: 5,
          option_name: "汽车"
        },
        {
          type: 6,
          option_name: "体育"
        },
        {
          type: 7,
          option_name: "财经"
        },
        {
          type: 8,
          option_name: "军事"
        },
        {
          type: 9,
          option_name: "国际"
        },
        {
          type: 10,
          option_name: "时尚"
        },
        {
          type: 11,
          option_name: "游戏"
        },
      ],
      option_bottom: [
        {
          type: 12,
          option_name: "旅游"
        },
        {
          type: 13,
          option_name: "历史"
        },
        {
          type: 14,
          option_name: "探索"
        },
        {
          type: 15,
          option_name: "美食"
        },
        {
          type: 16,
          option_name: "育儿"
        },
        {
          type: 17,
          option_name: "养生"
        },
        {
          type: 18,
          option_name: "故事"
        },
        {
          type: 19,
          option_name: "美文"
        },
      ]
    }
  },
  methods: {
    route_to(e) {
      this.$router.push({path: e})
    },
    move_to_bottom(e) {
      console.log(this.option_top)
      if (e !== 0) {
        console.log(e)
        for (let i = 0; i < this.option_top.length; ++ i) {
          if (this.option_top[i].type === e) {
            this.option_bottom.push(this.option_top[i]);
            this.option_top.splice(i, 1);
            console.log(i)
          }
        }
      }
    },
    move_to_top(e) {
      console.log(this.option_bottom)
      if (e !== 0) {
        console.log(e)
        for (let i = 0; i < this.option_bottom.length; ++ i) {
          if (this.option_bottom[i].type === e) {
            this.option_top.push(this.option_bottom[i]);
            this.option_bottom.splice(i, 1);
            console.log(i)
          }
        }
      }
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
