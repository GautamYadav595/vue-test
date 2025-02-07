<template>
  <div class="blog-post">
      <h3>{{ title }}</h3>
      <div v-html="content"></div>
  </div>
</template>

<script>
export default {
  name: 'BlogPost', // Fixed naming
  props: ['title', 'content'] // Ensure content is passed properly
};
</script>
