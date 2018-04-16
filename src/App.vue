<template>
  <div id="app">
    <top-container></top-container>
    <bottom-container></bottom-container>
  </div>
</template>

<script>
import TopContainer from './components/TopContainer'
import BottomContainer from './components/BottomContainer'

export default {
  name: 'App',
  data () {
    return {}
  },
  computed: {
  },
  methods: {
  },
  mounted () {
  },
  components: {
    'top-container': TopContainer,
    'bottom-container': BottomContainer
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
</style>
