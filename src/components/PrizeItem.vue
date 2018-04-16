<template>
  <section class="plate" v-bind:class="plateClass">
    <div class="gold" v-bind:class="`${itemvalue.size}-gold`"></div>
  </section>
</template>

<script>
export default {
  name: 'prize-item',
  data () {
    return {
    }
  },
  props: [
    'itemvalue'
  ],
  computed: {
    plateClass () {
      let obj = {}
      if (this.itemvalue.size === 'small') {
        if (this.itemvalue.position === 'left') {
          obj = {
            'top-left': true,
            'small-plate': true
          }
        } else {
          obj = {
            'top-right': true,
            'small-plate': true
          }
        }
      } else if (this.itemvalue.size === 'medium') {
        if (this.itemvalue.position === 'left') {
          obj = {
            'middle-left': true,
            'medium-plate': true
          }
        } else {
          obj = {
            'middle-right': true,
            'medium-plate': true
          }
        }
      } else if (this.itemvalue.size === 'large') {
        if (this.itemvalue.position === 'left') {
          obj = {
            'bottom-left': true,
            'large-plate': true
          }
        } else {
          obj = {
            'bottom-right': true,
            'large-plate': true
          }
        }
      }
      return obj
    }
  },
  methods: {

  },
  mounted () {

  }
}
</script>

<style scoped>
.plate {
  position: absolute;
  background: url(../assets/image/盘子.png);
  background-size: 100% 100%;
  z-index: 2;
}
.gold {
  position: absolute;
  top: 0;
  background: url(../assets/image/元宝.png);
  background-size: 100% 100%;
  z-index: 4;
}
.large-plate {
  width: 235px;
  height: 147px;
}
.medium-plate {
  width: calc(235px * 0.9);
  height: calc(147px * 0.9);
}
.small-plate {
  width: calc(235px * 0.8);
  height: calc(147px * 0.8);
}
.large-gold {
  width: 133px;
  height: 82px;
  left: 53px;
  top: -3px;
}
.medium-gold {
  width: calc(133px * 0.9);
  height: calc(82px * 0.9);
  left: calc(53px * 0.9);
  top: calc(-3px * 0.9);
}
.small-gold {
  width: calc(133px * 0.8);
  height: calc(82px * 0.8);
  left: calc(53px * 0.8);
  top: calc(-3px * 0.8);
}
.top-left {
  left: 160px;
  top: 180px;
}
.top-right {
  left: calc(100% - 235px * 0.8 - 160px);
  top: 180px;
}
.middle-left {
  left: 120px;
  top: 310px;
}
.middle-right {
  left: calc(100% - 235px * 0.9 - 120px);
  top: 310px;
}
.bottom-left {
  left: 80px;
  top: 480px;
}
.bottom-right {
  left: calc(100% - 235px - 80px);
  top: 480px;
}
</style>
