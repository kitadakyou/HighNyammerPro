<template>
<div class="thread">
  <div v-for="(post, idx) in posts">
      <post
        :name=post.name
        :icon=post.icon
        :body=post.body
        :groupName=post.groupName
        :dateTime=post.dateTime
      >
      </post>
  
  <hr v-if="idx !== posts.length - 1">
  </div>
</div>
</template>

<script>
import Post from '~/components/Post'

export default {
  components: {
    Post
  },
  props: {
      posts: {
          type: Array,
          required: true,
      }
  }
}
</script>
