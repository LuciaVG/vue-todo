<template>
  <div class="container">
      <ul>
        <li v-for="(task, index) in taskList"
            :key="index">
            <div class="row cosa  ">
              <div v-if="!task.done"  class="col s12 m3 center">
                <a @click="toggleTasks(task)" class="btn-floating btn-large waves-effect waves-light  lime accent-4"><i class="material-icons">done</i></a>
              </div>
              <div class="col s12 m9 cosa valign-wrapper txt">
                {{ task.name }}
              </div>
            </div>

        </li>
      </ul>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    },
    taskList: {
      type: Array,
      required: true
    }
  },
  methods: {
    toggleTasks (task) {
      this.$emit('completar', task)
    }
  }
}
</script>

<style media="screen">
@import url('https://fonts.googleapis.com/css?family=Open+Sans');

.cosa{
  height: 60px;
  vertical-align: middle;
}
.txt{
  font-family: 'Open Sans', sans-serif;
  font-size: 20px;
}
</style>
