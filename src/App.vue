<template>
  <div id="app">
    <input type="text" name="username">
    <input type="text" name="password">
    <button v-on:click="login">Greet</button> 
     <ul v-if="posts && posts.length">
    <li v-for="post of posts">
      <p><strong>{{post.title}}</strong></p>
      <p>{{post.body}}</p>
    </li>
  </ul>

  <ul v-if="errors && errors.length">
    <li v-for="error of errors">
      {{error.message}}
    </li>
  </ul>
  </div>
</template>

<script>
export default {
  name: "login",
  data() {
    return {
      posts: [],
      errors: []
    };
  },
  methods: {
    login: function(event) {
      var formData = new FormData(),
        url = "https://test-lighthouse.abpathfinder.net/~api/login";

      formData.append("source", "pathfinder");
      formData.append("loginUserName", "support");
      formData.append("loginPassword", "P@thf!nd3r");
      formData.append("timeZone", "America/Chicago");

      fetch(url, {
        method: "POST",
        body: formData
      })
        .then(function(response) {
          return response.text();
        })
        .then(function(response) {
          //bad JSON
          var obj = eval(`(${response})`);
        })
        .catch(function(err) {
          console.log(err);
        });
    }
  }
};
</script>

<style lang="scss">

</style>
