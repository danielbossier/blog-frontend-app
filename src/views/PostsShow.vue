<template>
  <div class="PostsShow">
    <div class="container">
      <h2>{{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <img v-bind:src="post.image" alt="post.title" />
      <br />
      <li v-if="$parent.getUserID() == post.user_id">
        <router-link v-bind:to="`/posts/${post.id}/edit`"><button>Edit Post</button></router-link>
      </li>
      <router-link to="/posts">Back to all posts.</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    axios.get("/posts/" + this.$route.params.id).then((response) => {
      this.post = response.data;
    });
  },
};
</script>
