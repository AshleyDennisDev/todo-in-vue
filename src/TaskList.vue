<script>
let id = 0;

export default {
  data() {
    return {
      newTodo: "",
      todos: [],
      buttonClass: "edit-update-btn",
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: id++,
        text: this.newTodo,
        done: false,
        editing: false,
      });
      this.newTodo = "";
    },
    buttonToggle(todo) {
      todo.editing = !todo.editing;
    },
    deleteTodo(todo) {
      this.todos = this.todos.filter((task) => task !== todo);
    },
  },
};
</script>

<template>
  <form @submit.prevent="addTodo">
    <input class="form" v-model="newTodo" />
    <button class="add-btn">Add Todo</button>
  </form>
  <div class="list-group">
    <div v-for="todo in todos" :key="todo.id">
      <input class="checkbox" type="checkbox" v-model="todo.done" />
      <span v-if="!todo.editing" :class="{ done: todo.done }">{{
        todo.text
      }}</span>
      <input
        class="form-2"
        v-if="todo.editing"
        type="text"
        v-model="todo.text"
      />
      <div class="btn-group">
        <button :class="buttonClass" @click="buttonToggle(todo)">
          {{ !todo.editing ? "Edit" : "Update" }}
        </button>
        <button class="delete-btn" @click="deleteTodo(todo)">Delete</button>
      </div>
    </div>
  </div>
</template>

<style>
.list-group {
  font-size: 2rem;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  padding-top: 2rem;
  padding-bottom: 3rem;
  display: flex;
  flex-direction: column;
}
.form {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande";
  font-size: 2rem;
  border: 0.25rem solid rgb(152, 151, 151);
  margin-top: 5rem;
  margin-right: 2rem;
  display: inline-flex;
  justify-content: center;
}

.form-2 {
  display: inline;
  font-size: 2rem;
  border: 4px solid rgb(152, 151, 151);
  margin-bottom: 1rem;
  margin-right: 2rem;
}
.add-btn {
  font-size: 2rem;
  background-color: rgb(250, 241, 229);
  border-radius: 1.5rem;
  padding-right: 10px;
  padding-left: 10px;
}
.edit-update-btn {
  font-size: 2rem;
  margin-right: 1rem;
  margin-left: 4rem;
  color: rgb(250, 241, 229);
  background-color: rgb(61, 58, 58);
  border-radius: 1.5rem;
  padding-left: 15px;
  padding-right: 15px;
}
.delete-btn {
  font-size: 2rem;
  margin-right: 1rem;
  margin-left: 1rem;
  color: rgb(250, 241, 229);
  background-color: rgb(61, 58, 58);
  border-radius: 1.5rem;
  padding-left: 15px;
  padding-right: 15px;
}
.btn-group {
  display: inline-flex;
  margin-bottom: 1rem;
  float:right;
}
.checkbox {
  height: 20px;
  width: 25px;
}
.done {
  text-decoration: line-through;
  color: grey;
}
</style>
