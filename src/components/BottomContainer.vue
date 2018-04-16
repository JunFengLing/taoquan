<template>
  <section class="container">
    <prize-item v-for="item in prizeList" v-bind:key="item.id" v-bind:itemvalue="item"></prize-item>
    <div class="ring-container" v-show="isgamestart" v-bind:class="positionObj">
      <div class="ring"></div>
      <div class="shade"></div>
    </div>
  </section>
</template>

<script>
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
      ]
    }
  },
  props: [
    'isgamestart'
  ],
  computed: {
    positionObj () {
      if (this.isgamestart) {
        return {
          'top-left': true
        }
      }
      return {
        'origin': true
      }
    }
  },
  methods: {
  },
  mounted () {
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
.ring-container {
  position: absolute;
  width: 242px;
  height: 150px;
  transition-property: top, left;
  transition-duration: 3s;
}
.ring {
  position: absolute;
  width: 230px;
  height: 117px;
  top: 0;
  left: calc((100% - 230px) / 2);
  background: url(../assets/image/套种圈.png);
  background-size: 100% 100%;
  z-index: 3;
}
.shade {
  position: absolute;
  width: 242px;
  height: 117px;
  bottom: 0;
  left: 0;
  background: url(../assets/image/套种圈阴影.png);
  background-size: 100% 100%;
}.
.origin {
  top: calc(100% - 150px);
  left: calc((100% - 242px) / 2);
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
