<template>
  <section class="charge-item" v-bind:style="chargeItemStyle">
    <div class="off-tag" v-show="isfirsttimecharge"></div>
    <div class="coin-label" v-bind:class="coinLableClass"></div>
    <div class="charge-btn"></div>
  </section>
</template>

<script>
export default {
  name: 'charge-item',
  data () {
    return {

    }
  },
  props: [
    'chargeitemvalue',
    'chargeitemindex',
    'isfirsttimecharge'
  ],
  computed: {
    chargeItemStyle () {
      let alignSelf = this.chargeitemindex < 2 ? 'flex-start' : 'flex-end'
      return {
        'alignSelf': alignSelf
      }
    },
    coinLableClass () {
      return `coin-label-${this.chargeitemindex + 1}`
    }
  },
  methods: {

  }
}
</script>

<style scoped>
.charge-item {
  position: relative;
  width: 210px;
  height: 276px;
  background: url(../assets/image/charge/金币背景.png);
  background-size: 100% 100%;
}
.off-tag {
  position: absolute;
  right: -2px;
  top: 0;
  width: 141px;
  height: 112px;
  background: url(../assets/image/charge/off标签.png);
  background-size: 100% 100%;
}
.coin-label {
  width: 169px;
  height: 156px;
  margin: 17px auto;
}
.coin-label-1 {
  background: url(../assets/image/charge/金币_1.png);
  background-size: 100% 100%;
}
.coin-label-2 {
  background: url(../assets/image/charge/金币_2.png);
  background-size: 100% 100%;
}
.coin-label-3 {
  background: url(../assets/image/charge/金币_3.png);
  background-size: 100% 100%;
}
.coin-label-4 {
  background: url(../assets/image/charge/金币_4.png);
  background-size: 100% 100%;
}
.charge-btn {
  width: 180px;
  height: 67px;
  margin: 0 auto;
  background: url(../assets/image/charge/按钮/按钮背景.png);
  background-size: 100% 100%;
}
</style>
