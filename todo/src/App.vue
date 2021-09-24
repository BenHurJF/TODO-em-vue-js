<template>
  <div class id="app">
    <div class="container grid-xs py-2">

      <img class="img-responsive img-todolist" src="@/assets/todolist.svg" alt="img-todolist">
      <h3 id="titulo">TodoList</h3>

      <form @submit.prevent="addTodo(todo)">
          <div class="input-group">
            <input v-model="todo.description" type="text" class="form-input" placeholder="Novo todo">
           
            <button class="btn btn-primary">Adicionar</button>
          </div>
      </form>
      
      <div class="todo-list"> 
         <todo v-for="t in todos" :key="t.id" :todo="t"/>

      </div>
    </div>
  </div>
   
</template>

<script>
import Todo from "./components/Todo.vue";

export default {
  name: 'app',
  components: { Todo },
  data() {
    return { todos: [

    ], todo: { checked: false } };
  },
  methods: {
    addTodo(todo) {
      todo.id = Date.now();
      this.todos.push(todo);
      this.todo = { checked : false }
    }
  }
};

</script>

<style scoped>

.img-todolist {
  max-width: 350px;
  max-height: 150px;

  text-align: center;
  margin-left: auto;
  margin-right: auto;
  margin-top: 70px;

  margin-bottom: 20px;
}

h3#titulo {
  text-align: center;
  margin-bottom: 20px;
}

.todo-list {
  padding-top: 2rem;
}

</style>