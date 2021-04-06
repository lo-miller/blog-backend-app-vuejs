<template>
  <div class="new-post">
    <h1>{{ message }}</h1>
    <!-- <div v-for="post in posts">
      {{post}}
    </div> -->
    <p>Title: <input type="text" v-model="title"></p>
    <p>Body: <input type="text" v-model="body"></p>
    <p>Image: <input type="text" v-model="image"></p>
    <button v-on:click="newPost">Create new post</button>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Create New Post",
      posts: [],
      title: "",
      body: "",
      image: "",
    };
  },
  created: function () {},
  methods: {
    newPost: function () {
      axios
        .post("/api/posts", {
          title: this.title,
          body: this.body,
          image: this.image,
        })
        .then((response) => {
          console.log(response.data);
          // this.posts = response.data;
        });
    },
  },
};
</script>


