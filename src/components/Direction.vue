<template>
  <div class="direction">
    <div class="direction-bg"></div>
    <div class="direction-label"></div>
    <div class="direction-pointer" v-bind:style="directionStyle"></div>
  </div>
</template>

<script>
export default {
  name: 'direction',
  data () {
    return {
      currDegree: 0
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
    }
  },
  methods: {
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
    }
  },
  mounted () {
    this.getDirection()
  }
}
</script>

<style scoped>
.direction {
  position: absolute;
  bottom: 0;
  left: 8px;
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
</style>
