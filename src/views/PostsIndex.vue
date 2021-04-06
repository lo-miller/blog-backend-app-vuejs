<template>
  <div class="posts">
    <h1>{{ message }}</h1>
    <div v-for="post in posts">
      {{post}}
    </div>
    <button v-on:click="indexPosts">Load posts</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Blog Posts",
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/api/posts").then((response) => {
        console.log(response.data);
        this.posts = response.data;
      });
    },
  },
};
</script>


