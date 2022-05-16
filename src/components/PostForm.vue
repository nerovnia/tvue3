<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <input class="input" type="text" placeholder="Name" v-model="post.title">
    <input class="input" type="text" placeholder="Description" v-model="post.body">
    <my-button style="align-self: flex-end; margin-top: 15px;" @click="createPost">Create</my-button>
  </form>
</template>

<script>
import MyButton from "./UI/MyButton"
export default {
  components: {
    MyButton
  },
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now(),
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    }  
  }
}
</script>

<style>
.input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}

form {
  display: flex;
  flex-direction: column;
}
</style>