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
    <div class="columns">
      <div v-if="post.replies.length !== 0" class="column is-11 is-offset-1 reply-container">
        <reply v-for="reply in post.replies" 
          :name=reply.name
          :icon=reply.icon
          :body=reply.body
          :groupName=reply.groupName
          :dateTime=reply.dateTime
          :depth=0
          :replies=reply.replies
        >
        </reply>
      </div>
    </div>
    <hr v-if="idx !== posts.length - 1">
  </div>
</div>
</template>

<script>
import Post from '~/components/Post'
import Reply from '~/components/Reply'

export default {
  components: {
    Post,
    Reply,
  },
  props: {
      posts: {
          type: Array,
          required: true,
      }
  }
}
</script>

<style>
.reply-container {
  margin-top: 1.5rem;
  background-color: #f5f5f5
}
</style>