<template>
  <div>
    <p>완료: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>노완료: {{todos.filter(todo => todo.done === false).length}}</p>
    <ul>
      <todo v-on:delete-todo="deleteTodo" v-for="todo in todos" v-bind:todo="todo"></todo>
    </ul>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIdx = this.todos.indexOf(todo);
      this.todos.splice(todoIdx, 1);
    }
  }
};
</script>
<style>
</style>
