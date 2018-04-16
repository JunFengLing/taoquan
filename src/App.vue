<template>
  <div id="app">
    <top-container></top-container>
    <div class="bottom-wrapper">
      <bottom-container v-bind:isgamestart="isGameStart"></bottom-container>
      <div class="bet-wrapper"><bet></bet></div>
      <div class="direction-wrapper"><direction></direction></div>
      <div class="power-wrapper"><power></power></div>
      <div class="ring" v-show="!isGameStart"></div>
      <div class="start-game-btn" v-show="!isGameStart" v-on:click="startGame()"></div>
    </div>
  </div>
</template>

<script>
import eventBus from './eventBus.js'

import TopContainer from './components/TopContainer'
import BottomContainer from './components/BottomContainer'
import Bet from './components/Bet'
import Direction from './components//Direction'
import Power from './components/Power'

export default {
  name: 'App',
  data () {
    return {
      isGameStart: false
    }
  },
  computed: {
  },
  methods: {
    startGame () {
      console.log('start game')
      this.isGameStart = true

      eventBus.$emit('notifyGameStart')
    }
  },
  mounted () {
  },
  components: {
    'top-container': TopContainer,
    'bottom-container': BottomContainer,
    'bet': Bet,
    'direction': Direction,
    'power': Power
  }
}
</script>

<style>
#app {
  display: flex;
  flex-direction: column;
  height: 1377px;
  text-align: center;
  font-size: 28px;
  font-weight: bold;
  color: #ffffff;
  background: url(./assets/image/背景.png) no-repeat;
  background-size: 100% 100%;
}
.bottom-wrapper {
  flex: 1;
  position: relative;
}
.bet-wrapper {
  position: absolute;
  bottom: 390px;
  left: calc((750px - 600px) / 2);
}
.direction-wrapper {
  position: absolute;
  bottom: 0;
  left: 8px;
}
.power-wrapper {
  position: absolute;
  bottom: 0;
  right: 2px;
}
.ring {
  position: absolute;
  width: 275px;
  height: 189px;
  top: calc(100% - 189px);
  left: calc((100% - 275px) / 2);
  background: url(./assets/image/圈.png);
  background-size: 100% 100%;
  z-index: 1;
}
.start-game-btn {
  position: absolute;
  bottom: 52px;
  left: calc((750px - 322px) / 2);
  width: 322px;
  height: 106px;
  background: url(./assets/image/开始游戏按钮.png);
  background-size: 100% 100%;
  z-index: 2;
}
</style>
