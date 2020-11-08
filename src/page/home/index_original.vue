<template>
<div class="home_container" @click="click">
  <router-link to="item">跳转其他页面</router-link>
  <div v-for="(item,index) of arr" :key="item.id">{{item}}/{{index}}</div>
  <div @click="addNum">自增啊啊啊</div>
  <div v-show="true"></div>
</div>
</template>

<script>
export default {
  name: 'home',
  data() {
    return {
      num: 123,
      arr: [123, 456111, 111, 45]

    }
  },
  // computed: {
  //   num() {
  //     return this.$store.state.num;
  //   }
  // },
  methods: {
    addNum() {
      let r = Math.floor(Math.random() * 10);
      console.log(r);
      this.$store.commit('ADD_NUM', r)
    },
    click() {
      console.log(123);

    },

  }
}
</script>

<style lang="less" scoped>
</style>
