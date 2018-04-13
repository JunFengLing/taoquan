<template>
  <section class="container">
    <div class="direction">
      <div class="direction-bg"></div>
      <div class="direction-label"></div>
      <div class="direction-pointer" v-bind:style="rotateStyle"></div>
    </div>
    <div class="start-game-btn" v-on:click="startGame()"></div>
    <div class="power">
      <div class="power-bg"></div>
      <div class="power-label"></div>
      <div class="power-block"></div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'container',
  data () {
    return {
      rotateDegree: 0,
      power: 0
    }
  },
  computed: {
    rotateStyle () {
      return {
        transform: `rotate(${this.rotateDegree}deg)`
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
        if (distanceX > 90) {
          this.rotateDegree = 90
        } else if (distanceX < -90) {
          this.rotateDegree = -90
        } else {
          this.rotateDegree = distanceX
        }
      })
    }
  },
  mounted () {
    this.getDirection()
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
  bottom: 0;
  right: 0;
  width: 104px;
  height: 42px;
  background: url(../assets/image/力度滑动按钮.png);
  background-size: 100% 100%;
  z-index: 2;
}
.power-block {
  position: absolute;
  bottom: 0;
  right: 0;
  width: 81px;
  height: 168px;
  margin: 0 calc((104px - 81px) / 2);
  background: url(../assets/image/力度滑块.png);
  background-size: 100% 100%;
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
