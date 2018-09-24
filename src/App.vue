<template>
  <div >
    <navbar
      :title="'My ToDo App'"/>

    <div class="content">
      <div class="row">
        <div class="col s12 m12">
          <div class="card">
            <div class="card-content black-text">
              <span class="card-title">Add a New Task</span>
              <form @submit.prevent="addTask">
                <div class="row center">
                  <div class="col s12 m11">
                    <input v-model="newTaskName" type="text" >
                  </div>
                  <div class="col s12 m1">
                    <button type="submit" class="btn waves-effect waves-light amber" >Add</button>
                  </div>
                </div>
              </form>
            </div>
            <div class="card-action">

              <div class="row">
                <div class="col s12 m6 center">
                  <span class="card-title">Pending</span>
                  <div class="divider"></div>
                  <tasks-list
                    :title="'Pendientes'"
                    :task-list="tasksPending"
                    @completar="toggleTasks"/>
                </div>
                <div class="col s12 m6 center">
                  <span class="card-title">Done</span>
                  <div class="divider"></div>
                  <tasks-list
                    :title="'Completados'"
                    :task-list="tasksComplete"
                    @completar="toggleTasks"/>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

  </div>
</template>

<script>
import TasksList from './components/TasksList'
import Navbar from './components/Navbar'

console.log("shfvhsd");

export default {
  components: {
    TasksList,
    Navbar
  },
  data () {
    return {
      newTaskName: '',
      tasks: [
      ]
    }
  },
  methods: {
    toggleTasks (task) {
      task.done = !task.done
      this.$localStorage.set('myTasks', JSON.stringify(this.tasks))
    },
    addTask () {
      if (!this.newTaskName) return
      this.tasks.push({ name: this.newTaskName, done: false })
      this.newTaskName = ''
      this.$localStorage.set('myTasks', JSON.stringify(this.tasks))
    }
  },
  mounted () {
  const todos = JSON.parse(this.$localStorage.get('myTasks'))
  if (todos) {
    this.tasks = todos
  }
},
  computed: {
    tasksPending () {
      return this.tasks.filter(task => !task.done)
    },
    tasksComplete () {
      return this.tasks.filter(task => task.done)
    }
  }
}
</script>

<style lang="css">
.content{
  padding: 5%;
}
</style>
