<template>
  <div class="main">
    <div class="photo">
      <div class="button">点击下载</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'download',
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
  position: relative;
  top: 0;
  width: 100%;
  height: 100vh;
  .photo {
    background: url(https://s1.pstatp.com/growth/mobile_landingpage/images/bg-wap.9710384a.png);
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    .button {
      border: 1px solid #56bfff;
      width: calc(100% - 30px);
      height: 37px;
      position: fixed;
      top: 80%;
      text-align: center;
      font-size: 12px;
      line-height: 34px;
      background: #56bfff;
      color: #fff;
      border-radius: 3px;
      font-weight: 400;
      box-shadow: 
      0 0 0 1px #2fb0ff, 
      inset 0 2px 0 hsla(0,0%,100%,0.2), 
      0 1px 0 1px rgba(0,0,0,0.2);
    }
  }
}

</style>
