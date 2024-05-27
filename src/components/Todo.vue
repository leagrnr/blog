<script>
  export default {
    data() {
      return {
        todoList: []
      }
    },
    methods: {
      // addTodo() {
      //   this.todos.push(this.newTodo)
      //   this.newTodo = ''
      // },
      // removeTodo(index) {
      //   this.todos.splice(index, 1)
      // }
    },

    mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos')
          .then(response => response.json())
          .then(json => this.todoList = json);
    }
    }


</script>

<template>
    <div class="todos">
      <div class="todo" v-for="todo in todoList" :key="todo.id">
        <input type="checkbox" v-bind:checked="todo.completed">
        <h3>{{ todo.title }}</h3>
      </div>
    </div>
</template>

<style scoped>
.todos {
  display: flex;
  flex-wrap: wrap;
}

.todo {
  width: 31%;
  box-sizing: border-box;
  border: 1px solid #aaa;
  padding: 5px;
  margin: 1%;
}
</style>