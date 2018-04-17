<template>
  <section class="container">
    <prize-item v-for="item in prizeList" v-bind:key="item.id" v-bind:itemvalue="item"></prize-item>
    <div class="ring" v-show="isgamestart" v-bind:class="ringClass"></div>
    <div class="shade" v-show="isgamestart" v-bind:class="shadeClass"></div>
  </section>
</template>

<script>
import eventBus from '../eventBus.js'

import PrizeItem from './prizeItem'

export default {
  name: 'container',
  data () {
    return {
      prizeList: [
        {
          id: 0,
          size: 'small',
          position: 'left'
        },
        {
          id: 1,
          size: 'small',
          position: 'right'
        },
        {
          id: 2,
          size: 'medium',
          position: 'left'
        },
        {
          id: 3,
          size: 'medium',
          position: 'right'
        },
        {
          id: 4,
          size: 'large',
          position: 'left'
        },
        {
          id: 5,
          size: 'large',
          position: 'right'
        }
      ],
      ringClass: 'ring-start',
      shadeClass: 'shade-start',
      currDegree: 0,
      currPower: 0.5
    }
  },
  props: [
    'isgamestart'
  ],
  computed: {
  },
  methods: {
    getClass () {
      if (this.currDegree > 0 && this.currDegree <= 20) {
        if (this.currPower < 0.33) {
          this.ringClass = 'ring-bottom-right'
          this.shadeClass = 'shade-bottom-right'
        } else if (this.currPower < 0.67) {
          this.ringClass = 'ring-middle-right'
          this.shadeClass = 'shade-middle-right'
        } else {
          this.ringClass = 'ring-top-right'
          this.shadeClass = 'shade-top-right'
        }
      } else if (this.currDegree > 20 && this.currDegree <= 40) {
        if (this.currPower < 0.33) {
          this.ringClass = 'ring-bottom-right'
          this.shadeClass = 'shade-bottom-right'
        } else {
          this.ringClass = 'ring-middle-right'
          this.shadeClass = 'shade-middle-right'
        }
      } else if (this.currDegree > 40 && this.currDegree <= 60) {
        this.ringClass = 'ring-bottom-right'
        this.shadeClass = 'shade-bottom-right'
      } else if (this.currDegree < 0 && this.currDegree >= -20) {
        if (this.currPower < 0.33) {
          this.ringClass = 'ring-bottom-left'
          this.shadeClass = 'shade-bottom-left'
        } else if (this.currPower < 0.67) {
          this.ringClass = 'ring-middle-left'
          this.shadeClass = 'shade-middle-left'
        } else {
          this.ringClass = 'ring-top-left'
          this.shadeClass = 'shade-top-left'
        }
      } else if (this.currDegree < -20 && this.currDegree >= -40) {
        if (this.currPower < 0.33) {
          this.ringClass = 'ring-bottom-left'
          this.shadeClass = 'shade-bottom-left'
        } else {
          this.ringClass = 'ring-middle-left'
          this.shadeClass = 'shade-middle-left'
        }
      } else if (this.currDegree < -40 && this.currDegree >= -60) {
        this.ringClass = 'ring-bottom-left'
        this.shadeClass = 'shade-bottom-left'
      }
    }
  },
  mounted () {
    eventBus.$on('notifyCurrDegree', params => {
      this.currDegree = params.currDegree
    })
    eventBus.$on('notifyCurrPower', params => {
      this.currPower = params.currPower
    })

    this.$watch('isgamestart', (newVal) => {
      if (newVal) {
        setTimeout(() => {
          this.getClass()
        }, 1000)
      }
    })
  },
  components: {
    'prizeItem': PrizeItem
  }
}
</script>

<style scoped>
.container {
  position: relative;
  height: 100%;
}
.ring {
  position: absolute;
  transition-property: width, height, top, left;
  transition-duration: 3s;
  background: url(../assets/image/套种圈.png);
  background-size: 100% 100%;
  z-index: 3;
}
.shade {
  position: absolute;
  transition-property: width, height, top, left;
  transition-duration: 3s;
  background: url(../assets/image/套种圈阴影.png);
  background-size: 100% 100%;
  z-index: 1;
}
.ring-start {
  width: 230px;
  height: 117px;
  top: calc(100% - 117px - 50px);
  left: calc((100% - 230px) / 2);
}
.shade-start {
  width: 242px;
  height: 117px;
  top: calc(100% - 117px);
  left: calc((100% - 242px) / 2);
}
.ring-top-left {
  width: calc(230px * 0.7);
  height: calc(117px * 0.7);
  left: 170px;
  top: 170px;
}
.shade-top-left {
  width: calc(242px * 0.7);
  height: calc(117px * 0.7);
  left: 164px;
  top: 210px;
}
.ring-top-right {
  width: calc(230px * 0.7);
  height: calc(117px * 0.7);
  left: 410px;
  top: 170px;
}
.shade-top-right {
  width: calc(242px * 0.7);
  height: calc(117px * 0.7);
  left: 406px;
  top: 210px;
}
.ring-middle-left {
  width: calc(230px * 0.8);
  height: calc(117px * 0.8);
  left: 140px;
  top: 290px;
}
.shade-middle-left {
  width: calc(242px * 0.8);
  height: calc(117px * 0.8);
  left: 134px;
  top: 350px;
}
.ring-middle-right {
  width: calc(230px * 0.8);
  height: calc(117px * 0.8);
  left: 430px;
  top: 290px;
}
.shade-middle-right {
  width: calc(242px * 0.8);
  height: calc(117px * 0.8);
  left: 430px;
  top: 350px;
}
.ring-bottom-left {
  width: calc(230px * 0.9);
  height: calc(117px * 0.9);
  left: 90px;
  top: 460px;
}
.shade-bottom-left {
  width: calc(242px * 0.9);
  height: calc(117px * 0.9);
  left: 84px;
  top: 510px;
}
.ring-bottom-right {
  width: calc(230px * 0.9);
  height: calc(117px * 0.9);
  left: 460px;
  top: 460px;
}
.shade-bottom-right {
  width: calc(242px * 0.9);
  height: calc(117px * 0.9);
  left: 454px;
  top: 510px;
}
</style>
