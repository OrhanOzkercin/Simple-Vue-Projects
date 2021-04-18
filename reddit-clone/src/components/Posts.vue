<template>
  <ul class="list-unstyled mt-3 mx-2">
    <li v-for="post in posts" :key="post.id" class="media mb-3">
      <img class="mr-3 rounded" :src="post.data.thumbnail" alt="icon" />
      <div class="media-body">
        <h5 class="mt-0 mb-1">
          <a :href="createUrl(post.data.permalink)" target="_blank">{{ post.data.title }}</a>
        </h5>
        <p>
          <span class="ups">{{ post.data.ups }} 🔼</span>
          <span class="d-block">Created by {{ post.data.author }} {{ formatDate(post.data.created) }} ago</span>
          <span class="badge badge-pill badge-secondary">{{ post.data.num_comments }} comments</span>
        </p>
      </div>
    </li>
  </ul>
</template>

<script>
import { formatDistanceToNow } from 'date-fns';
export default {
  name: 'Posts',
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    this.load();
  },
  methods: {
    load() {
      const url = 'https://www.reddit.com/r/Turkey/.json';
      fetch(url)
        .then((res) => res.json())
        .then((res) => (this.posts = res.data.children));
    },
    formatDate(date) {
      return formatDistanceToNow(new Date(date * 1000));
    },
    createUrl(path) {
      return `https://reddit.com${path}`;
    },
  },
};
</script>

<style>
.ups {
  display: block;
  color: aquamarine;
}
</style>
