<template>
  <div>
    <input v-model="newTodo" type="text" class="form-control" 
    placeholder="Введите название дела и нажмите enter"
    @keyup.enter="addTodo">

    <button class="btn btn-dark" @click="addTodo">Add</button> 

    <ul class="list-group">
      
      <li class="list-group-item"
       v-for="(todo, index) in todos" :key="index"
      :class="{ 'completed' : todo.completed }"
      :date="todo.date"> 

        <input class="checkbox-light" type="checkbox" 
        @click="todo.completed = !todo.completed">

          {{ index + 1 }} {{ todo.title }} 

        <span v-show="todo.completed">
          - {{ todo.date }}
        </span>

        <button class="btn cross" @click="deleteTodo(index)">
          &#10006;
        </button>

        <button class="btn" @click="todo.edit = !todo.edit">
          &#9998;
        </button>

        <input class="form-control" type="text" 
        v-show="todo.edit" v-model="todo.title" 
        @keyup.enter="todo.edit = !todo.edit">
        
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
          title: 'Read a book',
          completed: false,
          edit: false,
          date: new Date().toLocaleString()
        },
        { 
          id: 2,
          title: 'Walk the dog',
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
          id: this.newId,
          title: this.newTodo,
          completed: false,
          edit: false,
          date: new Date().toLocaleString()
        }
      );
      this.newTodo = '';
      this.newId += 1
    },
    deleteTodo(index) {
      this.todos.splice(index, 1)
    },
  },
}
</script>

<style lang="scss" scoped>
.cross {
  float: right;
}

.completed {
  color: #ccc;
  text-decoration: line-through;
}
</style>>
