<template>
  <section class="todo-list">
      <h3>To-do List</h3>
      <div class="all-todos">
        <div class="single-todo" v-for="todo,index in todos" :class="{ 'done':todo.done }" :key="index"
          @click="todo.done = !todo.done">
          <p>{{ todo.task }}</p>
        </div>
      </div>
      <button class="clear" v-if="todos.length > 0" @click="clearAll()">Clear All</button>
      <input type="text" placeholder="Add new to-do" v-model="newTodo.task">
      <button class="add" @click="addTodo()">Add</button>

      <div class="instructions">
          Help :
          <ul>
            <li>Click the to-do text to toggle between done / undone</li>
            <li>Use clear all button to remove all items</li>
            <li>Use the input field to add new to-dos</li>
          </ul>
      </div>
  </section>
</template>

<script>
export default {
  name: 'App',
  components: {
  },
  data() {
    return {
      todos: [
              {
                task: 'Nourrir le chat',
                done: false
              },
              {
                task: 'Sauver le monde',
                done: false
              },
              {
                task: 'Faire les courses',
                done: true
              },
              {
                task: 'Apprendre Vue js !',
                done: false
              }
            ],
      newTodo: {
        done: false
      }
    }
  },
  methods: {
    addTodo: function () {
      this.todos.push(this.newTodo);
      this.newTodo = { done: false };
    },
    clearAll: function () {
        this.todos = [];
    }
  }
}
</script>

<style>

</style>
