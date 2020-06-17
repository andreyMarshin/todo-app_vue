<template>
  <div>
    <div class="input-group mb-3">
      <input v-model="newTodo" type="text" class="form-control" 
      placeholder="Введите название дела и нажмите enter"
      @keyup.enter="addTodo">

      <div class="input-group-append">
        <button class="btn btn-dark" @click="addTodo">
          Add
        </button>
      </div>
    </div>

    <todo-item v-for="(todo, index) in todos"
    :key="index" :todo="todo" :index="index"
    :class="{ 'text-muted bg-light' : todo.completed }"
    @delete-todo="deleteTodo"/>

  </div>
</template>

<script>

import TodoItem from './TodoItem'

export default {
  components: {
    TodoItem
  },
  data() {
    return {
      newTodo: '',
      todos: [
        { 
          title: 'took',
          completed: false,
          edit: false,
          date: new Date().toLocaleString()
        },
        { 
          title: 'hook',
          completed: false,
          edit: false,
          date: new Date().toLocaleString()
        },
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push(
        {
          title: this.newTodo,
          completed: false,
          edit: false,
          date: new Date().toLocaleString()
        }
      );
      this.newTodo = ''
      this.newId += 1
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter(item => item !== todo)
    },
  },
}
</script>

