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
      var data = new FormData(),
        url = "https://test-lighthouse.abpathfinder.net/~api/login";
      data.append("source", "pathfinder");
      data.append("loginUserName", "support");
      data.append("loginPassword", "P@thf!nd3r");
      data.append("timeZone", "America/Chicago");

      var xhr = new XMLHttpRequest();
      xhr.open("POST", url, true);
      xhr.onload = function(x, y, z) {
        var json = JSON.parse({});
      };
      xhr.send(data);
    }
  }
};
</script>

<style lang="scss">

</style>
