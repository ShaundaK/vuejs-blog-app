<template>
  <div class="new">
    <h3> Create A New Post! </h3>
     
     <p>Title:<input type="text" v-model="newPost.title"></p>
     <p>Body:<input type="text" v-model="newPost.body"></p>
     <button v-on:click="addPost()">Add Post!</button>
    
  </div>
</template>

<script>
  var axios = require('axios');
  export default {

    data: function(){
      return {
        newPost: {title: "", body: ""}
      };
    },
    created: function() {

      axios.get('http://localhost:3000/api/posts').then(function(response) {
        console.log(response.data);
        this.posts = response.data;
      }.bind(this))
    },
    methods: {
      addPost: function() {
        var params = {
          title: this.newPost.title,
          body: this.newPost.body
        }
        axios.post('http://localhost:3000/api/posts', params).then(function(response) {
          console.log(response.data);
          this.posts.push(response.data);
        }.bind(this))
        console.log('add post');
        this.posts.push(this.newPost);
      },
    }
  };
</script>
