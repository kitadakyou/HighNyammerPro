<template>
  <div class="column is-9" id="TimelineContainer">
    <thread :posts=posts></thread>        
  </div>
</template>

<script>
import Thread from '~/components/Thread'

export default {
  components: {
    Thread
  },
  data() {
    return  {
      posts: [ 
        {
          name: "江藤光",
          icon: "https://avatars3.githubusercontent.com/u/4303909?s=32&v=4",
          body: "2019/12/14 3限\n\
コーヒーを飲んで過ごしました。\n\
Macの貸し出しがあったので対応しました。などなど",
          groupName: "シフト活動記録",
          dateTime: "2019/12/11 14:50",
          reply: "",
        },
        {
          name: "江藤光2",
          icon: "http://placehold.jp/32x32.png",
          body: "テスト本文2テスト本文2テスト本文2テスト本文2テスト本文2",
          groupName: "トピック",
          dateTime: "2019/12/11 14:50",
          reply: "",
        }
      ]
    }
  },
}
</script>

<style scoped>
  #TimelineContainer {
    padding: 3rem;
  }
</style>

<style>
  .textarea.reply-field {
    transition: all ease-in-out .5s;
    resize: none;
    max-height: 12rem;
    min-height: 3rem;
    height: 3rem;
    margin-top: 1rem;
  }

  .textarea.reply-field:focus {
    height: 12em;
  }
</style>
