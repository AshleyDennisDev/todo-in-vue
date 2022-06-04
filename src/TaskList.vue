<script>
let id = 0;

export default {
  data() {
    return {
      newTodo: "",
      todos: [],
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
  <ul class="list">
    <div class="list-group">
      <li v-for="todo in todos" :key="todo.id">
        <input class="checkbox" type="checkbox" v-model="todo.done" />
        <span v-if="!todo.editing" :class="{ done: todo.done }">{{
          todo.text
        }}</span>
        <input
          class="form-2"
          v-if="todo.editing"
          style="display: inline"
          type="text"
          v-model="todo.text"
        />
        <button
          class="edit-btn"
         v-if="!todo.editing" 
         @click="todo.editing = true"
        >
          Edit
        </button>
        <button
          class="update-btn"
          v-if="todo.editing"
          @click="todo.editing = false"
        >
          Update
        </button>
        <button class="delete-btn" @click="deleteTodo(todo)">Delete</button>
      </li>
    </div>
  </ul>
</template>

<style>
.list-group {
  padding: 20px;
  align-content: center;
}
.form {
  font-size: 2rem;
  border: 4px solid rgb(152, 151, 151);
  margin-top: 5rem;
  margin-right: 2rem;
  display: inline;
  justify-content: center;
}
.form-2 {
  font-size: 2rem;
  border: 4px solid rgb(152, 151, 151);
  margin-bottom: 1rem;
  margin-right: 2rem;
}
.add-btn {
  font-size: 2rem;
  background-color: bisque;
}
.edit-btn {
  font-size: 2rem;
  margin-right: 1rem;
  margin-left: 1rem;
  color: bisque;
  background-color: rgb(61, 58, 58);
}
.update-btn {
  font-size: 2rem;
  margin-right: 1rem;
  margin-left: 1rem;
  color: bisque;
  background-color: rgb(61, 58, 58);
}
.delete-btn {
  font-size: 2rem;
  margin-right: 1rem;
  margin-left: 1rem;
  color: bisque;
  background-color: rgb(61, 58, 58);
}
.list {
  list-style: none;
  font-size: 2rem;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
.checkbox {
  border-radius: 4rem;
}
.done {
  text-decoration: line-through;
  color: grey;
}
</style>
