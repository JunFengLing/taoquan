<template>
  <section class="bet-container">
    <div class="bet-text"></div>
    <div class="bet">
      <div
        class="bet-btn"
        v-for="item in betList"
        v-bind:key="item"
        v-bind:class="`bet-btn-${item}`"
        v-on:click="bet(item)"
      >
        <img v-bind:src="item.img"/>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'coin',
  data () {
    return {
      betList: [10, 20, 50]
    }
  },
  computed: {
  },
  methods: {
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
.bet-btn-10 {
  height: 76px;
  width: 156px;
  background: url(../assets/image/下注区_10铜板.png);
  background-size: 100% 100%;
}
.bet-btn-20 {
  height: 76px;
  width: 163px;
  background: url(../assets/image/下注区_20铜板.png);
  background-size: 100% 100%;
}
.bet-btn-50 {
  height: 76px;
  width: 155px;
  background: url(../assets/image/下注区_50铜板.png);
  background-size: 100% 100%;
}
</style>
