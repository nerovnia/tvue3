<template>
<div class="app">
  <div>
    <post-form @create="createPost"/>
    <post-list :posts="posts"/>
  </div>

</div>
<button>Click me!</button>
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
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
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