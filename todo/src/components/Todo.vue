<template>
  <div class="container">
    <h1 class="text-center">Player Score Counter</h1>
    <div class="card">
      <div class="card-body">
        <form>
          <div class="form-group">
            <label>New Todo</label>
            <input v-model="newTodo" type="text" class="form-control" placeholder="Learn Vue" />
            <small class="form-text text-muted">Enter new todo</small>
          </div>
          <button @click.prevent="addTodo" type="submit" class="btn btn-primary">Submit</button>
        </form>
        <h3 class="mt-3 text-center font-weight-bold">TODOS</h3>
        <ul class="list-group mt-5">
          <li v-for="(todo, index) in todos" :key="todo.title" class="list-group-item">
            <button
              @click="toggleDone(todo)"
              class="btn  rounded mr-3"
              :class="{ 'btn-success': !todo.done, 'btn-warning': todo.done }"
            >
              {{ todo.done ? 'UnDone' : 'Done' }}
            </button>
            <button @click="removeTodo(index)" class="btn btn-danger rounded mr-3">
              Remove
            </button>
            <span :class="{ done: todo.done }">{{ todo.title }}</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Todo',
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },

  mounted() {
    if (localStorage.todos) {
      this.todos = JSON.parse(localStorage.todos);
    }
  },

  watch: {
    todos: {
      handler() {
        localStorage.setItem('todos', JSON.stringify(this.todos));
      },
      deep: true,
    },
  },

  methods: {
    addTodo() {
      this.todos.push({ title: this.newTodo, done: false });
    },
    toggleDone(todo) {
      todo.done = !todo.done;
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>
