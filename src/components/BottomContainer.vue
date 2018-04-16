<template>
  <section class="container">
    <div class="start-game-btn" v-on:click="startGame()"></div>
    <div class="ring"></div>
    <direction></direction>
    <power></power>
  </section>
</template>

<script>
import Direction from './Direction'
import Power from './Power'

export default {
  name: 'container',
  data () {
    return {
    }
  },
  computed: {
  },
  methods: {
    startGame () {
      alert('start game')
    }
  },
  mounted () {
  },
  components: {
    'direction': Direction,
    'power': Power
  }
}
</script>

<style scoped>
.container {
  flex: 1;
  position: relative;
}
.start-game-btn {
  position: absolute;
  bottom: 52px;
  left: calc((750px - 322px) / 2);
  width: 322px;
  height: 106px;
  background: url(../assets/image/开始游戏按钮.png);
  background-size: 100% 100%;
  z-index: 1;
}
.ring {
  position: absolute;
  bottom: 0;
  left: calc((750px - 275px) / 2);
  width: 275px;
  height: 189px;
  background: url(../assets/image/圈.png);
  background-size: 100% 100%;
}
</style>
