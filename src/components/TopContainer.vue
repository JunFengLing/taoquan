<template>
  <section class="container">
    <div class="top-container">
      <div class="back-btn" v-on:click="back()"></div>
      <div class="title"></div>
    </div>
    <div class="bottom-container">
      <coin></coin>
      <div class="history" v-on:click="history()"></div>
      <div class="help-btn" v-on:click="help()"></div>
    </div>
  </section>
</template>

<script>
import Coin from './Coin'

export default {
  name: 'container',
  data () {
    return {}
  },
  computed: {
  },
  methods: {
    back () {
      alert('back')
    },
    history () {
      alert('history')
    },
    help () {
      alert('help')
    }
  },
  mounted () {
  },
  components: {
    'coin': Coin
  }
}
</script>

<style scoped>
.container {
}
.top-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 50px;
}
.bottom-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.title {
  width: 368px;
  height: 91px;
  margin-right: calc((750px - 368px) / 2);
  background: url(../assets/image/标题.png);
  background-size: 100% 100%;
}
.back-btn {
  width: 71px;
  height: 71px;
  margin-left: 16px;
  background-image: url(../assets/image/返回按钮.png);
  background-size: 100% 100%;
}
.history {
  width: 150px;
  height: 40px;
  margin-left: 190px;
  background-image: url(../assets/image/套圈记录.png);
  background-size: 100% 100%;
}
.help-btn {
  width: 60px;
  height: 60px;
  background-image: url(../assets/image/帮助按钮.png);
  background-size: 100% 100%;
}
</style>
