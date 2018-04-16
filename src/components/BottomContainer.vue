<template>
  <section class="container">
    <!-- <prize-item v-for="(item, index) in prizeList" v-bind:key="index"></prize-item> -->
    <div class="ring"></div>
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
          left: 0,
          top: 0
        }, 1, 2, 3, 4, 5]
    }
  },
  computed: {
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
  padding-top: 180px;
  height: calc(100% - 180px);
}
.ring {
  position: absolute;
  bottom: 0;
  left: calc((100% - 275px) / 2);
  width: 275px;
  height: 189px;
  background: url(../assets/image/圈.png);
  background-size: 100% 100%;
}
</style>
