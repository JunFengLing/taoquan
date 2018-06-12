<template>
  <section class="bet-container">
    <div class="bet-text"></div>
    <div class="bet">
      <div
        class="bet-btn"
        v-for="item in betList"
        v-bind:key="item"
        v-bind:style="betBtnImg(item)"
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
    betBtnImg (item) {
      return {
        'backgroundImage': `url(../../static/image/下注区_${item}铜板.png)`,
        'backgroundSize': '100% 100%'
      }
    },
    bet (item) {
      alert(`bet ${item}`)
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
  background-image: url(../../static/image/请选择下注金额.png);
  background-size: 100% 100%;
}
.bet {
  display: flex;
  justify-content: space-between;
}
.bet-btn {
  height: 76px;
  width: 156px;
}
</style>
