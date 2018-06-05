<template>
  <section class="charge-item" v-bind:style="chargeItemStyle" v-on:click="charge()">
    <div class="off-tag" v-show="isfirsttimecharge"></div>
    <div class="coin-label" v-bind:class="coinLableClass">
      <div class="coin-item-wrapper">
        <div class="coin-item-container" v-show="isfirsttimecharge">
          <div class="coin-item"></div>
          <div class="coin-item"
            v-for="(item, index) in coinItemList"
            v-bind:key="index"
            v-bind:class="coinItemClass(item)"
          >
          </div>
        </div>
        <div class="coin-item-container">
          <div class="coin-item coin-item-add"></div>
          <div class="coin-item"
            v-for="(item, index) in coinItemList"
            v-bind:key="index"
            v-bind:class="coinItemClass(item)"
          >
          </div>
        </div>
      </div>
    </div>
    <div class="charge-btn">
      <div class="money-item money-item-rmb"></div>
      <div class="money-item"
        v-for="(item, index) in moneyItemList"
        v-bind:key="index"
        v-bind:class="moneyItemClass(item)"
      >
      </div>
    </div>
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
    },
    coinItemList () {
      return `${this.chargeitemvalue.coin}`.split('')
    },
    moneyItemList () {
      return `${this.chargeitemvalue.money}`.split('')
    }
  },
  methods: {
    charge () {
      alert('charge')
    },
    coinItemClass (item) {
      return `coin-item-${item}`
    },
    moneyItemClass (item) {
      return `money-item-${item}`
    }
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
  z-index: 210;
}
.coin-label {
  position: relative;
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
  display: flex;
  justify-content: center;
  align-items: center;
  width: 180px;
  height: 67px;
  margin: 0 auto;
  background: url(../assets/image/charge/按钮/按钮背景.png);
  background-size: 100% 100%;
}
.coin-item-wrapper {
  position: absolute;
  bottom: 0;
}
.coin-item-container {
  display: flex;
  justify-content: center;
}
.coin-item {
  width: 27px;
  height: 36px;
}
.coin-item-add {
  background: url(../assets/image/charge/金币数字/+.png);
  background-size: 100% 100%;
}
.coin-item-0 {
  background: url(../assets/image/charge/金币数字/0.png);
  background-size: 100% 100%;
}
.coin-item-1 {
  background: url(../assets/image/charge/金币数字/1.png);
  background-size: 100% 100%;
}
.coin-item-2 {
  background: url(../assets/image/charge/金币数字/2.png);
  background-size: 100% 100%;
}
.coin-item-3 {
  background: url(../assets/image/charge/金币数字/3.png);
  background-size: 100% 100%;
}
.coin-item-4 {
  background: url(../assets/image/charge/金币数字/4.png);
  background-size: 100% 100%;
}
.coin-item-5 {
  background: url(../assets/image/charge/金币数字/5.png);
  background-size: 100% 100%;
}
.coin-item-6 {
  background: url(../assets/image/charge/金币数字/6.png);
  background-size: 100% 100%;
}
.coin-item-7 {
  background: url(../assets/image/charge/金币数字/7.png);
  background-size: 100% 100%;
}
.coin-item-8 {
  background: url(../assets/image/charge/金币数字/8.png);
  background-size: 100% 100%;
}
.coin-item-9 {
  background: url(../assets/image/charge/金币数字/9.png);
  background-size: 100% 100%;
}
.money-item {
  width: 26px;
  height: 34px;
}
.money-item-rmb {
  margin-right: 4px;
  background: url(../assets/image/charge/按钮/￥.png);
  background-size: 100% 100%;
}
.money-item-0 {
  background: url(../assets/image/charge/按钮/0.png);
  background-size: 100% 100%;
}
.money-item-1 {
  background: url(../assets/image/charge/按钮/1.png);
  background-size: 100% 100%;
}
.money-item-2 {
  background: url(../assets/image/charge/按钮/2.png);
  background-size: 100% 100%;
}
.money-item-3 {
  background: url(../assets/image/charge/按钮/3.png);
  background-size: 100% 100%;
}
.money-item-4 {
  background: url(../assets/image/charge/按钮/4.png);
  background-size: 100% 100%;
}
.money-item-5 {
  background: url(../assets/image/charge/按钮/5.png);
  background-size: 100% 100%;
}
.money-item-6 {
  background: url(../assets/image/charge/按钮/6.png);
  background-size: 100% 100%;
}
.money-item-7 {
  background: url(../assets/image/charge/按钮/7.png);
  background-size: 100% 100%;
}
.money-item-8 {
  background: url(../assets/image/charge/按钮/8.png);
  background-size: 100% 100%;
}
.money-item-9 {
  background: url(../assets/image/charge/按钮/9.png);
  background-size: 100% 100%;
}

</style>
