<template>
<main>
  <div class="columns">
    <div id="SidemenuContainer" class="column is-3">
      <b-menu>
        <b-menu-list label="グループ">
            <b-menu-item v-for="group in groups"
                :label=group.name
                tag="router-link"
                :to=group.to>
            </b-menu-item>
        </b-menu-list>
      </b-menu>
    </div>
    <div class="column is-9" id="TimelineContainer">
      <thread :posts=posts>
      </thread>        
    </div>
  </div>
</main>
</template>

<script>
import Thread from '~/components/Thread'

export default {
  components: {
    Thread
  },
  data() {
    return  {
      groups: [
        {
          name: "トピック",
          to: "/group/1",
        },
        {
          name: "シフト活動記録",
          to: "/group/2",
        }

      ],
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
  #SidemenuContainer {
    text-align: right;
    background: #f5f5f5;
    padding-top: 2rem;
    padding-left: 2rem;
  }

  #TimelineContainer {
    padding: 3rem;
  }

  .post-header {
    margin-bottom: 0;
  }
  img.user-icon {
    margin-top: .5rem;
  }
  .post-user-name {
    font-size: 1rem;
  }
  .post-group {
    font-size: .8rem;
  }
  .post-group .post-group-guide {
    color: #606770;
    margin-right: .6rem;
  }
  pre.post-body {
    padding-top: .5rem;
    padding-bottom: 0;
  }
  pre.post-body-top {
    background-color: white;
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
