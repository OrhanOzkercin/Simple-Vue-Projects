<template>
  <div class="home">
    <Posts msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import Posts from '@/components/Posts.vue';

export default {
  name: 'Home',
  components: {
    Posts,
  },
};
</script>
