<template>
  <section class="task-item">
    <div class="task-description">{{ taskitemvalue.description }}</div>
    <div class="task-btn" v-bind:class="taskBtnClass" v-on:click="doTask()"></div>
  </section>
</template>

<script>
export default {
  name: 'task-item',
  data () {
    return {

    }
  },
  props: [
    'taskitemvalue'
  ],
  computed: {
    taskBtnClass () {
      return this.taskitemvalue.isComplete ? 'complete-task-btn' : 'not-complete-task-btn'
    }
  },
  methods: {
    doTask () {

    }
  }
}
</script>

<style scoped>
.task-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 592px;
  height: 99px;
  margin: 0 auto;
  background: url(../assets/image/task/任务栏背景.png);
  background-size: 100% 100%;
}
.task-description {
  width: 330px;
  margin-left: 100px;
  text-align: left;

}
.task-btn {
  width: 136px;
  height: 54px;
  margin-right: 10px
}
.complete-task-btn {
  background: url(../assets/image/task/已兑换按钮.png);
  background-size: 100% 100%;
}
.not-complete-task-btn {
  background: url(../assets/image/task/去完成按钮.png);
  background-size: 100% 100%;
}
</style>
