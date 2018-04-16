<template>
  <section class="bet-container">
    <div class="bet-text"></div>
    <div class="bet">
      <div
        class="bet-btn"
        v-for="item in betList"
        v-bind:key="item.id"
        v-bind:style="betBtnStyle(item.width)"
        v-on:click="bet(item.id)"
      >
        <img v-bind:src="item.img"/>
      </div>
    </div>
  </section>
</template>

<script>
import screenUtil from '../utils/screenUtil.js'

export default {
  name: 'coin',
  data () {
    return {
      betList: [
        {
          id: 10,
          img: require('../assets/image/下注区_10铜板.png'),
          width: 156
        },
        {
          id: 20,
          img: require('../assets/image/下注区_20铜板.png'),
          width: 163
        },
        {
          id: 50,
          img: require('../assets/image/下注区_50铜板.png'),
          width: 155
        }
      ]
    }
  },
  computed: {
  },
  methods: {
    betBtnStyle (width) {
      return {
        width: width * screenUtil.screenRatio + 'px'
      }
    },
    bet (amount) {
      alert(`bet ${amount}`)
    }
  },
  mounted () {

  }
}
</script>

<style scoped>
.bet-container {
  width: 600px;
}
.bet-text {
  width: 537px;
  height: 60px;
  margin: 0 auto 14px;
  background: url(../assets/image/请选择下注金额.png);
  background-size: 100% 100%;
}
.bet {
  display: flex;
  justify-content: space-between;
}
.bet-btn {
  height: 76px;
}
.bet-btn img {
  width: 100%;
  height: 100%;
}
</style>
