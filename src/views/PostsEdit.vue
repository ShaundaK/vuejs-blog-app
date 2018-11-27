<template>
  <div class="login">
    <div class="container">
      <form v-on:submit.prevent="submit()">
        <h1>Create A New Blog Post</h1>
        <ul>
          <li class="text-danger" v-for="error in errors">{{ error }}</li>
        </ul>
        <div class="form-group">
          <label>Title:</label>
          <input type="text" class="form-control" v-model="text">
        </div>
        <div class="form-group">
          <label>Body:</label>
          <input type="text" class="form-control" v-model="text">
        </div>
        <input type="submit" class="btn btn-primary" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {

created: function() {
  console.log('in created');
 axios.get('http://localhost:3000/api/posts/' + this.$route.params.id).then(response => {
  console.log(response.data);
  this.title = response.data.title
  this.body = response.data.body
  })
 }
};
</script>