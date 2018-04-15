<template>
  <section class="container">
    <div class="direction">
      <div class="direction-bg"></div>
      <div class="direction-label"></div>
      <div class="direction-pointer" v-bind:style="directionStyle"></div>
    </div>
    <div class="start-game-btn" v-on:click="startGame()"></div>
    <div class="power">
      <div class="power-bg"></div>
      <div class="power-label" v-bind:style="powerStyle"></div>
      <div class="power-block" v-bind:style="powerStyle"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'container',
  data () {
    return {
      currDegree: 0,
      currPower: 0.5
    }
  },
  computed: {
    directionStyle () {
      if ((this.currDegree > 0 && this.currDegree <= 90) || (this.currDegree < 0 && this.currDegree >= -90)) {
        return {
          transform: `rotate(${this.currDegree}deg)`
        }
      }
      return {}
    },
    powerStyle () {
      return {
        top: (1 - this.currPower) * 100 + '%'
      }
    }
  },
  methods: {
    startGame () {
      alert('start game')
    },
    getDirection () {
      let direction = document.querySelector('.direction')
      let startX, endX, distanceX

      direction.addEventListener('touchstart', event => {
        startX = event.targetTouches[0].pageX
      })

      direction.addEventListener('touchmove', event => {
        endX = event.targetTouches[0].pageX
      })

      direction.addEventListener('touchend', event => {
        distanceX = endX - startX
        console.log(`direction distanceX: ${distanceX}`)

        if (distanceX > 90) {
          this.currDegree = 90
        } else if (distanceX < -90) {
          this.currDegree = -90
        } else {
          this.currDegree = distanceX
        }
        console.log(`current degree: ${this.currDegree}`)
      })
    },
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
    this.getDirection()
    this.getPower()
  },
  components: {

  }
}
</script>

<style scoped>
.container {
  position: absolute;
  width: 100%;
  height: 168px;
  bottom: 0;
  left: 0;
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
}
.direction {
  flex: 1;
  position: relative;
  width: 188px;
  height: 92px;
}
.direction-bg {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 188px;
  height: 92px;
  background: url(../assets/image/方向转盘背景.png);
  background-size: 100% 100%;
}
.direction-label {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 77px;
  height: 39px;
  margin: 0 calc((188px - 77px) / 2);
  background: url(../assets/image/方向.png);
  background-size: 100% 100%;
  z-index: 2;
}
.direction-pointer {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 40px;
  height: 99px;
  margin: 0 calc((188px - 40px) / 2);
  background: url(../assets/image/方向指针.png);
  background-size: 100% 100%;
  z-index: 1;
  transform-origin: 50% 100%;
}
.power {
  flex: 1;
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
.start-game-btn {
  width: 322px;
  height: 106px;
  margin-bottom: 40px;
  background: url(../assets/image/开始游戏按钮.png);
  background-size: 100% 100%;
}
</style>
