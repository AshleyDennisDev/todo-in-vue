<script>
import TaskListVue from "./TaskList.vue";

export default {
  components: {
    TaskListVue,
  },
};
</script>

<template>
  <h1>Daily To Dos</h1>
  <TaskListVue />
</template>

<style>
h1 {
  display: flex;
  justify-content: space-around;
}
#app {
  background: rgb(249, 200, 165);
  margin: 4rem 20px;
  padding: 1rem;
  padding-top: 0;
  box-shadow: 0 6px 4px 0 rgba(0, 0, 0, 0.2),
    0 2.5rem 5rem 1rem rgba(0, 0, 0, 0.1);
  max-width: 60rem;
  display: flex;
  flex-direction: column;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande";
  color: rgb(61, 58, 58);
}

@media screen and (min-width: 550px) {
  #app {
    padding: 4rem;
  }
}
#app > * {
  max-width: 50rem;
  margin-left: auto;
  margin-right: auto;
}
</style>
