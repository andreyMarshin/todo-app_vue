<template>
  <div>
    <input v-model="newTodo" type="text" class="form-control" placeholder="Введите название дела и нажмите enter"
    @keyup.enter="addTodo">
    <button class="btn btn-dark" @click="addTodo">Add</button> 

    <ul class="list-group">
      <li class="list-group-item mt4"
       v-for="(todo, index) in todos" :key="index"
      > 
        {{ index + 1 }} {{ todo.title }}
        <button class="btn cross" @click="deleteTodo(index)">
          &#10006;
        </button>
        <button class="btn" @click="todo.edit = !todo.edit">
          &#9998;
        </button>
        <input class="form-control" type="text" v-if="todo.edit" 
        v-model="todo.title">
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
          title: 'Reading the books',
          edit: false,
        },
        { 
          id: 2,
          title: 'Working from home',
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
      console.log(index)
      this.todos.splice(index, 1)
    },
    editingTodo() {
      console.log()
    }
  },
}
</script>

<style>

body {
  background-color: #ccc
}

.cross {
  float: right;
}
</style>