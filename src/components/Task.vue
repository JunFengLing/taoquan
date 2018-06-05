<template>
  <section class="task" v-show="isShow">
    <div class="task-container">
      <div class="task-title"></div>
      <div class="close-btn" v-on:click="close()"></div>
      <task-item
        v-for="(item, index) in taskItemList"
        v-bind:key="index"
        v-bind:taskitemvalue="item"
      >
      </task-item>
    </div>
  </section>
</template>

<script>
import eventBus from '../eventBus.js'

import TaskItem from './TaskItem'

export default {
  name: 'task',
  data () {
    return {
      isShow: false,
      taskItemList: [
        {
          description: '每天完成5局游戏，获得10铜板奖励',
          isComplete: false
        },
        {
          description: '每天完成5局游戏，获得10铜板奖励',
          isComplete: false
        },
        {
          description: '每天完成5局游戏，获得10铜板奖励',
          isComplete: false
        },
        {
          description: '每天完成5局游戏，获得10铜板奖励',
          isComplete: true
        }
      ]
    }
  },
  computed: {

  },
  methods: {
    close () {
      this.isShow = false
    }
  },
  components: {
    'task-item': TaskItem
  },
  mounted () {
    eventBus.$on('NotifyShowTask', () => {
      this.isShow = true
    })
  }
}
</script>

<style scoped>
.task {
  position: absolute;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
  z-index: 200;
}
.task-container {
  position: relative;
  width: 656px;
  height: 868px;
  margin: 254px auto;
  background: url(../assets/image/task/背景.png);
  background-size: 100% 100%;
}
.task-title {
  position: relative;
  top: -30px;
  width: 285px;
  height: 95px;
  margin: 0 auto;
  background: url(../assets/image/task/任务标题.png);
  background-size: 100% 100%;
}
.close-btn {
  position: absolute;
  top: -14px;
  right: -14px;
  width: 75px;
  height: 76px;
  background: url(../assets/image/charge/关闭按钮.png);
  background-size: 100% 100%;
}
</style>
