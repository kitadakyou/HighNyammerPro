<template>
  <div class="reply">    
    <div class="columns reply-container">
      <div :class="replyColumnClass">
        <div class="columns reply-header">
          <div class="column  is-narrow">
              <div style="width: 32px;">
                  <img width=32 height=32 class="user-icon" :src="icon">
              </div>
          </div>
          <div class="column">
              <p class="reply-user-name">{{ name }}</p>
              <div class="reply-body">
                <pre class="reply-body reply-body-top">{{ body }}</pre>
              </div>
          </div>
        </div>
        <b-field>
            <b-input
              type="textarea"
              v-model="replyText"
              placeholder="返信を書く…"
              custom-class="reply-field"
            >
            </b-input>
        </b-field>
        <div class="level">
          <div class="level-left">
            
            <span class="attachment-icon" @click="fileAttach">
              <b-icon
                icon="attachment"
              >
              </b-icon>
            <input type="file" class="file-elem" style="display:none" @change="handleFiles">
            </span>
             <span v-if="attachmentFileName !== ''" class="attachment-file-name">{{ attachmentFileName}} <span @click="removeAttachFile"><b-icon icon="close-circle" size="is-small" type="is-dark"></b-icon></span></span>
          </div>
          <div class="level-right">
              <b-button @click="alert('clicked')" :disabled="isDisabledSendButton"><b-icon icon="send"></b-icon><span>送信</span></b-button>
          </div>
        </div>
      </div>
    </div>
    <reply v-for="_reply in replies" 
      :name=_reply.name
      :icon=_reply.icon
      :body=_reply.body
      :groupName=_reply.groupName
      :dateTime=_reply.dateTime
      :depth=depth+1
      :replies=_reply.replies
    />
  </div>
</template>

<script>
import Reply from '~/components/Reply'

export default {
  name: 'reply',
  components: {
    Reply,
  },
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
      depth: {
        type: Number,
        required: true,
      },
      replies: {
        type: Array,
        required: true,
      }
  },
  data() {
      return  {
        replyText: "",
        attachmentFileName: "",          
      }
  },
  computed: {
    isDisabledSendButton: function() {
      return this.replyText === "";
    },
    replyColumnClass: function() {
      console.log(this.depth);
      return "column is-" + (12 - this.depth) + " is-offset-" + this.depth;
    },
  },
  methods: {
    fileAttach: function() {        
      let fileElem = this.$el.querySelector('.file-elem');
      console.log(fileElem);
      fileElem.click();
    },
    handleFiles: function(e) {        
      this.attachmentFileName = e.srcElement.files[0].name;
    },
    removeAttachFile: function() {
      let fileElem = this.$el.querySelector('.file-elem');
      fileElem.value = '';
      this.attachmentFileName = '';
    }
  }
}
</script>

<style scoped>
  .reply-container {
    border-bottom: solid .4rem #ffffff;
    margin-top: 0;  
  }

  .reply-header {
    margin-bottom: 0;
  }
  img.user-icon {
    margin-top: .5rem;
  }
  .reply-user-name {
    font-size: 1rem;
  }
  .reply-group {
    font-size: .8rem;
  }
  .reply-group .reply-group-guide {
    color: #606770;
    margin-right: .6rem;
  }
  pre.reply-body {
    font-size: inherit;
    font-family: -apple-system, BlinkMacSystemFont, "Helvetica Neue", "ヒラギノ角ゴ ProN W3", Hiragino Kaku Gothic ProN, Arial, "メイリオ", Meiryo, sans-serif;
    padding-top: .5rem;
    padding-bottom: 0;
    padding-left: 0;
    white-space: pre-wrap;
  }
  span.attachment-file-name {
    font-size: .8rem;
    margin-left: .5rem;
    padding: .2rem;
    background-color: #f5f5f5
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
