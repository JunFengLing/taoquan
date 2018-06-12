<template>
  <section class="coin">
    <div class="coin-icon"></div>
    <div class="coin-amount">{{ coinAmount }}</div>
    <div class="add-coin" v-on:click="charge()"></div>
  </section>
</template>

<script>
import eventBus from '../eventBus.js'

export default {
  name: 'coin',
  data () {
    return {
      coinAmount: 98765432
    }
  },
  computed: {
  },
  methods: {
    charge () {
      eventBus.$emit('NotifyShowCharge')
    }
  },
  mounted () {

  }
}
</script>

<style scoped>
.coin {
  position: relative;
  width: 260px;
  height: 50px
}
.coin-icon {
  position: absolute;
  left: 0;
  width: 48px;
  height: 50px;
  background-image: url(../../static/image/金币.png);
  background-size: 100% 100%;
  z-index: 110;
}
.add-coin {
  position: absolute;
  right: 0;
  width: 50px;
  height: 50px;
  background-image: url(../../static/image/加金币按钮.png);
  background-size: 100% 100%;
  z-index: 110;
}
.coin-amount {
  position: absolute;
  left: 12px;
  bottom: 6px;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 236px;
  height: 40px;
  line-height: 40px;
  color: #ffa509;
  letter-spacing: 2px;
  background-image: url(../../static/image/金币数背景.png);
  background-size: 100% 100%;
}
.coin-number {
  width: 17px;
  height: 25px;
}
</style>
