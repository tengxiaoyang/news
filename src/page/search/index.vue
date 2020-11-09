<template>
  <div class="main">
    This is from route page 
    <div>{{ name | capitalize }}</div>
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
  z-index: 1;
}

</style>
