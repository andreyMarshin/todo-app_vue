<template>
  <div>
    <input v-model="newTodo" type="text" class="form-control" placeholder="Введите название дела и нажмите enter"
    @keyup.enter="addTodo">
    <button class="btn btn-dark" @click="addTodo">Add</button> 

    <ul class="list-group">
      <li class="list-group-item mt4"
       v-for="(todo, index) in todos" :key="index" @click="deleteTodo(index)">
        {{ index + 1 }} {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newId: 3,
      newTodo: '',
      todos: [
        { 
          id: 1,
          title: 'Walk the dog',
          edit: false,
        },
        { 
          id: 2,
          title: 'Read a book',
          edit: false,
        },
      ]
    }
  },
  methods: {
    addTodo() {
      this.todos.push(
        {
          id: this.newId,
          title: this.newTodo,
          edit: false,
        }
      );
      this.newTodo = '';
      this.newId += 1
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    }
  },
}
</script>

<style>

body {
  background-color: #ccc
}
</style>