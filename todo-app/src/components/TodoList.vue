<template>
  <div>
    <p>완료: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>노완료: {{todos.filter(todo => todo.done === false).length}}</p>
    <ul>
      <todo @delete-todo="deleteTodo" @complete-todo="completeTodo" v-for="todo in todos" :key="todo" v-bind:todo="todo"></todo>
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
    },
    completeTodo(todo) {
      const todoIdx = this.todos.indexOf(todo);
      this.todos[todoIdx].done = true;
    }
  }
};
</script>
<style>
</style>
