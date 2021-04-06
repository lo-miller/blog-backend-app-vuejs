<template>
  <div class="show-post">
    <h1>{{ message }}</h1>
    <div>
      <p>Title: {{post.title}} </p>
      <p>Body: {{post.body}} </p>
      <p>Image URL: {{post.image}} </p>
      <img v-bind:src="post.image">
      </div>
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
      post: {},
    };
  },
  created: function () {
    axios.get(`/api/posts/${this.$route.params.id}`).then((response) => {
      console.log(response.data);
      this.post = response.data;
    });
  },
  methods: {
    showPosts: function () {
      // axios.get("/api/posts" + this.$route.params.id).then((response) => {
      //   console.log(response.data);
      //   this.post = response.data;
      // });
    },
  },
};
</script>


