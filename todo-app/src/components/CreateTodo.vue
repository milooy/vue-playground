<template>
  <div>
    <button @click="openForm" v-show="!isCreating">+추가</button>
    <div class="content" v-show="isCreating">
      <div class="field">
        <label>Title</label>
        <input v-model="titleText" type="text" ref="title" defaultValue="" />
      </div>
      <div class="field">
        <label>Project</label>
        <input v-model="projectText" type="text" ref="project" defaultValue="" />
      </div>
      <div class="">
        <button @click="sendForm()">만들기</button>
        <button @click="closeForm()">닫기</button>
      </div>
    </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    data() {
      return {
        titleText: '',
        projectText: '',
        isCreating: false,
      }
    },
    methods: {
      openForm() {
        this.isCreating = true;
      },
      closeForm() {
        this.isCreating = false;
      },
      sendForm() {
        console.log("센드폼")
        if(this.titleText.length > 0 && this.projectText.length > 0) {
          const title = this.titleText;
          const project = this.projectText;
          console.log(title, project)
          this.$emit('create-todo', {
            title, project, done: false,
          });
          this.titleText = '';
          this.projectText = '';
        }
        this.isCreating = false;
      }
    }
  }
</script>
