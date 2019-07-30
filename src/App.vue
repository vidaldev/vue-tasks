<template>
  <div id="app">
    <!-- Header -->
    <b-navbar toggleable="lg" type="light" class="navbar_header" fixed="top">
      <b-navbar-brand href="#" class="brand_site"><img src="./assets/logo.png" alt="Logo"></b-navbar-brand>
      <b-navbar-nav class="ml-auto">
        <b-nav-item href="#" disabled>{{ name }}</b-nav-item>
        <b-nav-item href="https://github.com/vidaldev/vue-tasks">Github</b-nav-item>
      </b-navbar-nav>
    </b-navbar>

    <!-- Section -->
    <section>
      <div class="section_input">
        <b-input-group size="lg" class="mb-3" prepend="Task">
          <b-form-input v-model="newTask.title" placeholder="Task"></b-form-input>
          <b-form-input v-model="newTask.time" placeholder="Time (in number)" @focus="focustime"></b-form-input>
          <b-input-group-append>
            <b-button size="sm" text="Button" variant="success" @click="addTask"><span class="addtask_text">Add</span><span class="addtask_icon">+</span></b-button>
            <b-button size="sm" text="Button" variant="danger" @click="cancel"><span class="cancel_text">Cancel</span><span class="cancel_icon">-</span></b-button>
          </b-input-group-append>
        </b-input-group>
      </div>

      <div class="section_title">
        <h2>To-Do list <span v-show="tasks.length">(Press the task to delete)</span></h2>
        <div class="section_list">
            <b-list-group v-show="tasks.length">
              <b-list-group-item v-for="(t,index) in tasks" :key="index" href="#" @click="removeTask(index)">
                {{ t.title }}
                <div class="left-task">{{ t.time }}</div>
              </b-list-group-item>              
            </b-list-group>
            <div v-show="!tasks.length"> 
              There are no registered tasks ... not yet. Cheer up!
            </div>
            <div v-show="tasks.length" class="total_time">
              Total time: <span>{{ totalTime }}</span>
            </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      name: 'Jose Vidal',
      tasks: [],
      newTask: {
        title: '',
        time: 0
      }
    }
  },
  created () {
    this.tasks = JSON.parse(localStorage.getItem('tasks')) || []
  },
  methods: {
    addTask () {
      if (!this.newTask.title || !this.newTask.time) {return}

      if (isNaN(this.newTask.time)) {
        this.$bvModal.msgBoxOk('The time field must be numeric only.', {
          title: 'Error',
          size: 'sm',
          buttonSize: 'sm',
          okVariant: 'danger',
          headerClass: 'p-2 border-bottom-0',
          footerClass: 'p-2 border-top-0',
          centered: true
        })
        return
      }
      
      this.tasks.push({
        title: this.newTask.title,
        time: this.newTask.time
      })

      localStorage.setItem("tasks", JSON.stringify(this.tasks)) 

      this.newTask.title = ''
      this.newTask.time = 0
    },

    removeTask (index) {
      this.tasks.splice(index, 1)
      localStorage.setItem("tasks", JSON.stringify(this.tasks))
    },

    cancel () {
      this.newTask.title = ''
      this.newTask.time = 0
    },

    focustime () {
      console.log('Aqui debe seleccionar todo el campo');
    }
  },
  computed: {
    totalTime () {
      if (!this.tasks.length) { return 0 }
      
      let total = 0
      
      this.tasks.forEach(t => {
         total += parseInt(t.time)
      })
      
      return total
    }
  }
}
</script>

<style lang="scss">
  @import url('scss/custom.scss');
</style>
