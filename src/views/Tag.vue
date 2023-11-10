<template>
  <div class="tag">
    Tag: {{ tag }}
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList :posts="filteredList"/>
    </div>
    <div v-else><Spinner/></div>
  </div>
</template>

<script>

import getPosts from "@/composables/getPosts";
import PostList from "@/components/PostList.vue";
import Spinner from "@/composables/Spinner.vue";
import {computed} from "vue";
import {useRoute} from "vue-router";

export default {
  components: {Spinner, PostList},
  props: ['tag'],
  setup(){
    const { posts, error, load } = getPosts()
    load()

    const route = useRoute()
    console.log('')
    const filteredList = computed(() => {
      return posts.value.filter(post => post.tags.includes(route.params.tag))
    })
    return { posts, error, filteredList }
  },

}
</script>

<style>

</style>
