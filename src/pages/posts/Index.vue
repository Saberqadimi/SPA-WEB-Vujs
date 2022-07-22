<template>
  <h1>Posts</h1>
</template>

<script>
import axios from "axios";

export default {
    name : "PostIndex",

  setup() {
    function getUsers() {
      axios
        .get("https://jsonplaceholder.typicode.com/posts")
        .then(function (response) {
          // handle success
          console.log(response.data);
        })
        .catch(function (error) {
          // handle error
          console.log(error);
        });
    }

    getUsers()
  },
};
</script>

<style>
</style>