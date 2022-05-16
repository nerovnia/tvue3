<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <my-input 
      type="text" 
      placeholder="Name" 
      v-model="post.title"
    >
    </my-input>
    <my-input 
      type="text" 
      placeholder="Description" 
      v-model="post.body"
    >
    </my-input>
    <my-button 
      style="align-self: flex-end; margin-top: 15px;" 
      @click="createPost"
    > Create
    </my-button>
  </form>
</template>

<script>
import MyInput from './UI/MyInput.vue'
export default {
  data() {
    return {
      post: {
        title: "",
        body: ""
      }
    };
  },
  methods: {
    createPost() {
      this.post.id = Date.now(),
        this.$emit("create", this.post);
      this.post = {
        title: "",
        body: ""
      };
    }
  },
  components: { MyInput }
}
</script>

<style>
form {
  display: flex;
  flex-direction: column;
}
</style>