<template>
  <div class="wrapper">
    <h1 class="title">POST LIST</h1>
    <ul class="post-list">
      <li v-for="post in posts" :key="post.id" class="post-item">
        <strong>{{ post.id }}. {{ post.title }}</strong>
        <span class="post-body"> — {{ post.body }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import axios from 'axios'

export default {
  name: 'PostList',
  setup() {
    const posts = ref([])

    onMounted(async () => {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts')
        posts.value = response.data
      } catch (error) {
        console.error('Error fetching posts:', error)
      }
    })

    return { posts }
  }
}
</script>

<style>
body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #74ebd5, #9face6);
  min-height: 100vh;
  padding: 20px;
}

.wrapper {
  text-align: left;
  margin-left: 40px;
}

.title {
  color: white;
  font-size: 32px;
  font-weight: bold;
  margin-bottom: 20px;
  text-transform: uppercase;
  background-color: crimson;
  padding: 8px 16px;
  border-radius: 6px;
  display: inline-block;
  box-shadow: 2px 4px 8px rgba(0,0,0,0.3);
}

.post-list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.post-item {
  margin-bottom: 20px;
  text-align: left;
  line-height: 1.6;
  background: white;
  padding: 12px;
  border-radius: 6px;
  box-shadow: 1px 2px 6px rgba(0,0,0,0.15);
  white-space: normal; 
  display:block;
  width: 500%;/* ✅ natural wrap, dili stanza */
}
.post-item strong {
  font-weight: bold;
  font-size: 18px;   /* ✅ title klaro ug bigger */
  color: #111;
}
.post-body {
  font-weight: normal;
  color: #333;
}
</style>





