<template>
  <section class="power">
    <div class="power-bg"></div>
    <div class="power-label" v-bind:style="powerStyle"></div>
    <div class="power-block" v-bind:style="powerStyle"></div>
  </section>
</template>

<script>
export default {
  name: 'power',
  data () {
    return {
      currPower: 0.5
    }
  },
  computed: {
    powerStyle () {
      return {
        top: (1 - this.currPower) * 100 + '%'
      }
    }
  },
  methods: {
    getPower () {
      const power = document.querySelector('.power')
      const maxPowerHeight = power.clientHeight
      const minPowerHeight = document.querySelector('.power-label').clientHeight
      let minPower = minPowerHeight / maxPowerHeight
      let startY, endY, distanceY
      let currentPower

      console.log(`max power height: ${maxPowerHeight}`)
      console.log(`min power height: ${minPowerHeight}`)

      power.addEventListener('touchstart', event => {
        startY = event.targetTouches[0].pageY
      })

      power.addEventListener('touchmove', event => {
        endY = event.targetTouches[0].pageY
      })

      power.addEventListener('touchend', event => {
        distanceY = endY - startY
        console.log(`power distanceY: ${distanceY}`)

        currentPower = this.currPower - distanceY / maxPowerHeight

        if (currentPower > 1) {
          this.currPower = 1
        } else if (currentPower < minPower) {
          this.currPower = minPower
        } else {
          this.currPower = currentPower
        }
        console.log(`current power: ${this.currPower}`)
      })
    }
  },
  mounted () {
    this.getPower()
  }
}
</script>

<style scoped>
.power {
  position: relative;
  width: 104px;
  height: 168px;
  overflow: hidden;
}
.power-bg {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 81px;
  height: 168px;
  margin: 0 calc((104px - 81px) / 2);
  background: url(../assets/image/力度条背景.png);
  background-size: 100% 100%;
}
.power-label {
  position: absolute;
  right: 0;
  width: 104px;
  height: 42px;
  background: url(../assets/image/力度滑动按钮.png);
  background-size: 100% 100%;
  transition: top 1s;
  z-index: 2;
}
.power-block {
  position: absolute;
  right: 0;
  width: 81px;
  height: 168px;
  margin: 0 calc((104px - 81px) / 2);
  background: url(../assets/image/力度滑块.png);
  background-size: 100% 100%;
  transition: top 1s;
  z-index: 1;
}
</style>
