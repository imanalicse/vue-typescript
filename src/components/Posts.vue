<template>
  <div>Posts pages</div>
  <ul class="posts">
      <li v-for="post in posts" v-bind:key="post.id">
            {{post.title}}
      </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Posts',
  data() {
      return {
          posts: []
      }
  },
 mounted() {
      fetch('https://jsonplaceholder.typicode.com/posts', {
          method: 'GET'
      })
      .then(response => response.json())
      .then(data => {
          this.posts = data;
          console.log(data);
      })
      .catch(err => console.log(err.message));
  }
});
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
