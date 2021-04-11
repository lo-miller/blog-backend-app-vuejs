<template>
  <div class="edit-post">
    <h1>{{ message }}</h1>
    <!-- {{post}} -->
    <form v-on:submit.prevent="updatePost(post)">
      <p>Title: <input type="text" v-model="post.title"></p>
      <p>Body: <input type="text" v-model="post.body"></p>
      <p>Image: <input type="text" v-model="post.image"></p>
      <input type="submit" value="Update Post"> 
    </form>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Edit This Post",
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
    updatePost: function () {
      axios
        .patch(`/api/posts/12`, {
          title: this.post.title,
          body: this.post.body,
          image: this.post.image,
        })
        .then((response) => {
          console.log(response.data);
          this.$router.push(`/posts/12/`);
        });
    },
  },
};
</script>


