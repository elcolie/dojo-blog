<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post"/>
    </div>

  </div>
</template>

<script>

import SinglePost from "@/components/SinglePost.vue";
import {computed, onMounted, onUnmounted, onUpdated} from "vue";

export default {
  components: { SinglePost },
  props: ['posts'],
}
</script>

<style>

</style>
