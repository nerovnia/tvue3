<template>
  <div class="app">
    <h1>Page with posts</h1>
    <my-button 
      @click="showDialog"
      style="margin: 15px 0;"
    >Create post
    </my-button> 
    <my-dialog
      v-model:show="dialogVisible"
    >
      <post-form 
        @create="createPost"
      />
    </my-dialog>
    <post-list 
      :posts="posts" 
      @remove="removePost"
    />
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";

export default {
  components: {
    PostList, PostForm
  },
  data() {
    return {
      posts: [
        { id: '1', title: 'JavaScript 0', body: 'Description 0'},
        { id: '2', title: 'JavaScript 1', body: 'Description 1'},
        { id: '3', title: 'JavaScript 2', body: 'Description 2'},
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
</style>