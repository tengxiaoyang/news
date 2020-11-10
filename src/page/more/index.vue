<template>
  <div class="main">
    <div class="header">
      <div class="back" @click="route_to('/')"></div>
      频道管理
    </div> 
    <div class="middle">
      <div class="title">点击删除以下频道</div>
      <div class="content">
        <div class="item"></div>
      </div>
    </div>
    <div class="bottom"></div>
  </div>
</template>

<script>
export default {
  name: 'more',
  data() {
    return {
      name: 'helloworld vue'
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
}

</style>
