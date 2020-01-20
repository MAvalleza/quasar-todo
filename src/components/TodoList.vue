<template lang="pug">
  q-page
    q-input(square outlined v-model="newTodo" label="Add New Task")
      template(v-slot:after)
        q-btn(round dense icon="add" color="primary" @click="addTask")
    q-separator
    q-list(bordered)
      q-item(
        clickable
        v-ripple
        v-for="(todo, key) in todos"
        :key="key"
        :active="todo.isCompleted"
        active-class="completed-task"
      )
        q-item-section(side top)
          q-checkbox(v-model="todo.isCompleted" @input="completeTask(todo.isCompleted)")
        q-item-section
          q-item-label {{ todo.title }}
        q-item-section(v-if="todo.isCompleted" side top)
          q-btn(
            flat
            dense
            round
            icon="delete"
            color="negative"
            @click="deleteTask(key)"
          )
    //- q-page-sticky(position="bottom-right").q-pa-lg
    //-   q-btn(fab icon="add" color="primary" @click="showAddTask")

      
    
</template>


<script>
export default {
  name: 'TodoList',

  data () {
    return {
      newTodo: '',
      todos: [
        { 
          title: 'Clean the house',
          isCompleted: false
        },
        {
          title: 'Feed the dogs',
          isCompleted: false
        }
        
      ]
    };
  },
  methods: {
    addTask () {
      let task = {
        title: this.newTodo,
        isCompleted: false
      };
      this.todos.push(task);
      this.newTodo = '';
      this.$q.notify({
        message: 'Successfully added new task!',
        color: 'positive'
      });
    },
    completeTask (isCompleted) {
      if (isCompleted) {
        this.$q.notify({
          message: 'Task is completed!',
          color: 'primary'
        });
      }
    },
    deleteTask(index) {
      this.todos.splice(index, 1);
      this.$q.notify({
        message: 'Task is successfully deleted!',
        color: 'positive'
      });
    }
  }
}
</script>

<style scoped>
.completed-task {
  background: #c8e4f7;
}
</style>