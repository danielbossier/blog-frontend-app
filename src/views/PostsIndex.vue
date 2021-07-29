<template>
  <div class="allposts">
    <div class="card-deck">
      <div class="card">
        <div
          v-for="post in posts"
          :key="post.id"
          v-bind:class="{ selected: post === currentPost }"
          v-on:click="currentPost = post"
        >
          <img class="card-img-top" v-bind:src="post.image" alt="Card image cap" />
          <div class="card-body">
            <h2 class="card-title">Title: {{ post.title }}</h2>
            <p class="card-text">Body: {{ post.body }}</p>
            <p class="card-text"><small class="text-muted"></small></p>
          </div>

          <!-- <router-link v-bind:to="`/posts/${post.id}`">
            <h2>Title: {{ post.title }}</h2>
            <p>Body: {{ post.body }}</p>
            <img v-bind:src="post.image" alt="post.title" />
          </router-link> -->
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card {
  width: 50%;
}
body {
  color: green !important;
}
</style>

<script>
import Vue2Filters from "vue2-filters";

import axios from "axios";

export default {
  mixins: [Vue2Filters.mixin],

  data: function () {
    return {
      message: "Here are all the Posts!",
      posts: [],
      currentPost: {},
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/posts").then((response) => {
        this.posts = response.data;
        console.log("All posts:", this.posts);
      });
    },
  },
};
</script>
