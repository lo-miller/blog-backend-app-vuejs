<template>
  <div class="show-post">
    <h1>{{ message }}</h1>
    <div>
      <p>Title: {{post.title}} </p>
      <p>Body: {{post.body}} </p>
      <p>Image URL: {{post.image}} </p>
      <p>User: {{post.user_id}} </p>
      <img v-bind:src="post.image">
      <br>
      <p>post.user_id: {{post.user_id}}</p>
      <p>$parent.userId(): {{$parent.userId()}}</p>
      <div v-if="post.user_id == $parent.userId()">
        <router-link v-bind:to="`/posts/${this.$route.params.id}/edit`">Edit This Post</router-link>
      </div>

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


