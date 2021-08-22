<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <h2>ToDo List</h2>
      </div>
    </div>
    <div class="row">
      <div class="d-flex flex-row bd-highlight justify-content-center mb-3">
        <div class="p-2 bd-highlight">
          <input
            type="text"
            class="form-control"
            name="todo"
            id="todo"
            v-model="todo"
            @keyup.enter="addTodo"
            placeholder="Your To Do List"
          />
        </div>
        <div class="p-2 bd-highlight">
          <button class="btn btn-primary" @click="addTodo()">Add Todo</button>
        </div>
      </div>
    </div>
    <div class="row">
      <div class="d-flex flex-row bd-highlight justify-content-center mb-3">
        <table class="table" v-if="todos.length > 0">
          <thead>
            <tr>
              <th scope="col">No</th>
              <th scope="col">To Do</th>
              <th scope="col">Action</th>
            </tr>
          </thead>
          <tbody v-for="(todo, index) in todos" :key="index">
            <td scope="row">{{ index + 1 }}</td>
            <td>{{ todo }}</td>
            <td>
              <button
                type="button"
                class="btn btn-danger"
                @click="deleteTodo(index)"
              >
                Delete
              </button>
            </td>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: ['Learn Vue', 'Learn React'],
      todo: "",
    };
  },
  created() {
    this.loadLocalStorage();
  },
  watch: {
    todos() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
  },
  methods: {
    loadLocalStorage() {
      const ls = JSON.parse(localStorage.getItem("todos"));
      // console.log(ls);
      if (ls == null) {
        return;
      }
      this.todos = ls;
      console.log(this.todos);
    },
    addTodo() {
      this.todos.push(this.todo);
      this.todo = "";
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
  },
};
</script>

<style scoped></style>
