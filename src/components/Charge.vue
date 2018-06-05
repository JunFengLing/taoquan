<template>
  <section class="charge" v-show="isShow">
    <div class="charge-container">
      <div class="charge-title" v-bind:class="chargeTitle"></div>
      <div class="close-btn" v-on:click="close()"></div>
      <div class="charge-item-contianer">
        <charge-item
          v-for="(item, index) in chargeItemList"
          v-bind:key="index"
          v-bind:chargeitemvalue="item"
          v-bind:chargeitemindex="index"
          v-bind:isfirsttimecharge="isFirstTimeCharge"
        >
        </charge-item>
      </div>
    </div>
  </section>
</template>

<script>
import eventBus from '../eventBus.js'

import ChargeItem from './ChargeItem'

export default {
  name: 'charge',
  data () {
    return {
      isShow: false,
      isFirstTimeCharge: false,
      chargeItemList: [
        {
          money: 6,
          coin: 36000
        },
        {
          money: 68,
          coin: 36000
        },
        {
          money: 168,
          coin: 36000
        },
        {
          money: 618,
          coin: 36000
        }
      ]
    }
  },
  computed: {
    chargeTitle () {
      return this.isFirstTimeCharge ? 'first-time-charge' : 'not-first-time-charge'
    }
  },
  methods: {
    close () {
      this.isShow = false
    }
  },
  components: {
    'charge-item': ChargeItem
  },
  mounted () {
    eventBus.$on('NotifyShowCharge', () => {
      this.isShow = true
    })
  }
}
</script>

<style scoped>
.charge {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 200;
}
.charge-container {
  position: relative;
  width: 615px;
  height: 797px;
  margin: 290px auto;
  background: url(../assets/image/charge/弹窗背景.png);
  background-size: 100% 100%;
}
.charge-title {
  position: relative;
  top: -30px;
  width: 285px;
  height: 95px;
  margin: 0 auto;
}
.first-time-charge {
  background: url(../assets/image/charge/首充标题.png);
  background-size: 100% 100%;
}
.not-first-time-charge {
  background: url(../assets/image/charge/标题_充值.png);
  background-size: 100% 100%;
}
.close-btn {
  position: absolute;
  top: -14px;
  right: -14px;
  width: 75px;
  height: 76px;
  background: url(../assets/image/charge/关闭按钮.png);
  background-size: 100% 100%;
}
.charge-item-contianer {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  width: 454px;
  height: 584px;
  margin: 0 auto;
}
</style>
