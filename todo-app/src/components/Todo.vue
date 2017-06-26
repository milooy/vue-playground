<template>
  <li>
    <div class="content" v-show="!isEditing">
      <h2>{{todo.title}}</h2>
      <div>{{todo.project}}</div>
      <button v-on:click="showForm">수정</button>
      <button v-on:click="deleteTodo(todo)">삭제</button>
      <div v-show="todo.done">~~완료~~</div>
      <div v-show="!todo.done">~~하는중~~</div>
    </div>
    <div class="content" v-show="isEditing">
      <div class="field">
        <label>Title</label>
        <input type="text" v-model="todo.title" />
      </div>
      <div class="field">
        <label>Project</label>
        <input type="text" v-model="todo.project" />
      </div>
      <div class="">
        <button class="" v-on:click="hideForm">닫기</button>
      </div>
    </div>
  </li>
</template>

<script type="text/javascript">
  export default {
    props: ['todo'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
      deleteTodo(todo) {
        this.$emit('delete-todo', todo);
      },
      completeTodo(todo) {
        this.$emit('complete-todo', todo);
      }
    }
  };
</script>
