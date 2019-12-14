<template>
    <div class="post">
        <div class="columns post-header">
        <div class="column  is-narrow">
            <div style="width: 32px;">
                <img class="user-icon" :src="icon">
            </div>
        </div>
        <div class="column">
            <p class="post-user-name">{{ name }}</p>
            <p class="post-group"><span class="post-group-guide">投稿先グループ</span><span class="post-group-name">{{ groupName }}</span></p>
        </div>      
        </div>  
        <div class="post-body">
          <pre class="post-body post-body-top">
            {{ body }}
          </pre>
        </div>
        <b-field>
            <b-input
                type="textarea"
                v-model="reply"
                placeholder="返信を書く…"
                custom-class="reply-field">
            </b-input>
        </b-field>
    </div>    
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            required: true,
        },
        icon: {
            type: String,
            required: true,
        },
        body: {
            type: String,
            required: true,
        },
        groupName: {
            type: String,
            required: true,
        },
        dateTime: {
            type: String,
            required: true,
        },
    },
    data() {
        return  {
          reply: ""
        }
    },
}
</script>

<style scoped>
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
    padding-left: 0;
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
  }

  .textarea.reply-field:focus {
    height: 12em;
  }
</style>
