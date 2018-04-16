<template>
  <section class="prize-item">
    <div class="gold" v-bind:style="goldStyle"></div>
    <div class="plate" v-bind:style="plateStyle"></div>
  </section>
</template>

<script>
import screenUtil from '../utils/screenUtil.js'

export default {
  name: 'prize-item',
  data () {
    return {
    }
  },
  computed: {
    goldStyle () {
      return {
        width: 133 * screenUtil.screenRatio + 'px',
        height: 82 * screenUtil.screenRatio + 'px'
      }
    },
    plateStyle () {
      return {
        width: 235 * screenUtil.screenRatio + 'px',
        height: 147 * screenUtil.screenRatio + 'px'
      }
    }
  },
  methods: {

  },
  mounted () {

  }
}
</script>

<style scoped>
.prize-item {
  position: absolute;
  left: 150px;
  top: 300px;
}
.gold {
  /* position: absolute;
  top: 0; */
  background: url(../assets/image/元宝.png);
  background-size: 100% 100%;
}
.plate {
  /* position: absolute;
  bottom: 0; */
  background: url(../assets/image/盘子.png);
  background-size: 100% 100%;
}
</style>
