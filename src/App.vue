<script>
import TaskListVue from './TaskList.vue';

export default{
  components: {
    TaskListVue
  }
}
</script>

<template>
<TaskListVue />
</template>


<style>
#app {
  background: rgb(190, 206, 174);
  margin: 4rem 8rem 4rem 8rem;
  padding: 1rem;
  padding-top: 0;
  position: relative;
  box-shadow: 0 6px 8px 0 rgba(0, 0, 0, 0.2), 0 2.5rem 5rem 5rem rgba(0, 0, 0, 0.1);
  max-width: 60rem;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
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