<template>
  <div class="home">
    <h1>Home</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="posts"/>
      <TagCloud :posts="posts"/>
    </div>
    <div v-else><Spinner/></div>
  </div>
</template>

<script>

import PostList from "@/components/PostList.vue";
import getPosts from "@/composables/getPosts";
import Spinner from "@/composables/Spinner.vue";
import TagCloud from "@/components/TagCloud.vue";

export default {
  name: 'HomeView',
  components: {TagCloud, PostList, Spinner},
  setup(){
    const { posts, error, load } = getPosts()
    load()
    return { posts, error }
  }
}
</script>
<style>
.home {
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px;
}
</style>
