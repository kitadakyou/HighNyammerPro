<template>
  <div id="TimelineContainer">
    <thread :posts=posts>
    </thread>        
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
          name: "近藤 秀樹",
          icon: "http://milais.highnyammer.com/uploads/cache/attachments/1fb1a4ebe9a91d0c32b71a30d31ffb7e.jpg",
          body: "2019/12 の稼働の予定についてです．諸般の事情から，近藤は 12/23 からお休みを取ることになりました．(まあ休みといってもやることは山盛りなんですけども)\n\
12/23 には授業があり，みなさんは 12/24 から冬期休業となっていると思います．大変恐縮ですが，12/23 の授業はみなさんだけでうまく回していただけますよう御協力をお願いしたく思います．\n\
\n\
新年は 1/6 からとなります．\n\
\n\
どうぞよろしくお願いします．",
          groupName: "アナウンス",
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
