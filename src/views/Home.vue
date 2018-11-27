<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="post in posts">
      <h3>{{post.title}}</h3>
      <h3>{{post.body}}</h3>
    </div>
  </div>
</template>

<style>
</style>

<script>
var axios = require('axios')
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      posts: []
    };
  },
  created: function() {
    console.log('in the create function');
    console.log(this)
    axios.get('http://localhost:3000/api/posts').then(function(response) {
      console.log(response.data);
      this.posts = response.data
    }.bind(this))
  },
  methods: {},
  computed: {}
};
</script>
