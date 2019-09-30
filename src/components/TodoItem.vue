<template>
  <div  class="list-group-item">
    <input class="checkbox-light" type="checkbox" 
    @click="todo.completed = !todo.completed">

    {{ index + 1}} {{ todo.title }} 

    <span v-show="todo.completed">
      - {{ todo.date }}
    </span>

    <button class="btn float-right text-secondary" 
    @click="deleteTodo(todo)">
      &#10006;
    </button>

    <button class="btn" @click="todo.edit = !todo.edit">
      &#9998;
    </button>

    <input class="form-control bg-light" type="text" 
    v-show="todo.edit" v-model="todo.title" 
    @keyup.enter="todo.edit = !todo.edit">
  </div>
</template>

<script>
export default {
  props: ['todo', 'index'],
  methods: {
    deleteTodo(todo) {
      this.$emit('delete-todo', todo)
    }
  }
}
</script>
