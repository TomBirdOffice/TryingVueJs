<template>
  <div class="posts">
    <ul v-for="post in posts" class="list">
      <li v-for="(content, key) in post">
        {{ key }} : {{ content }}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: "component2",
    data() {
      return {
        posts: {}
      }
    },
    created(){
      let vm = this
      this.$http
        .get('https://jsonplaceholder.typicode.com/posts')
        .then(function(response){
          vm.posts = response.data
        })
    }
  }

</script>

<style>

</style>
