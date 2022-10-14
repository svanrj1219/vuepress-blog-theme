<template>
  <div ref="valineBox" id="post-comment">
    <div class="comment-head">
      <div class="comment-headline">
        <img src="https://amoshk.top/img/icon/blog_message-emoji.svg" width="36px">&nbsp;
        评论
      </div>
      <div class="tips">
        <div style="margin-bottom:12px; ">✒️ 支持
          <a target="_blank" href="https://guides.github.com/features/mastering-markdown">Markdown</a>
          格式
        </div>
        <div style="margin-bottom:12px; ">🖼️ 头像与邮箱绑定 <a target="_blank" href="https://gravatar.com">Gravatar</a>
          服务
        </div>
        <div style="margin-bottom:0px; ">📬 邮箱能够收到回复提醒（可能会在垃圾箱内）</div>
      </div>
    </div>
    <div id="vcomments"></div>
  </div>
</template>

<script>

export default {
  mounted() {
    setTimeout(() => {
      this.loadComment();
    }, 500)
  },
  watch: {
    '$route'(to, from) {
      if (to.path !== from.path) {
        // 切换页面时重新载入评论
        setTimeout(() => {
          this.loadComment()
        }, 500)
      }
    }
  },
  methods: {
    clearComment() {
      const oDiv = document.querySelector('#vcomments');
      oDiv && oDiv.remove();
    },
    async loadComment() {
      const Valine = await import('valine')
      this.clearComment();
      const oCommentContent = document.createElement('div');
      oCommentContent.setAttribute('id', 'vcomments');
      this.$refs.valineBox.appendChild(oCommentContent);
      new Valine.default({
        el: '#vcomments',
        path: window.location.pathname,
        appId: "Tbia0reeR8O6XGLhD1bgvD6k-MdYXbMMI",
        appKey: "3bV42LdcCtb35ASQzrHv1VmC",
        placeholder: "留下你想说的话吧...",
        serverURLs: "https://tbia0ree.api.lncldglobal.com",
        visitor: true,
        avatar: 'robohash',
      })
    }
  }
}
</script>
<style lang="stylus">
#vcomments {
  margin 20px

  .vpanel {
    border-radius 15px
    background #f7f7f5

    .vwrap {
      border none
    }

    .vheader {
      input {
        color #444
      }
    }

    .vsubmit {
      background #27ae60
      color white
    }
  }

  .vquote {
    background #f9f9f7
    border-radius 15px

    .vat {
      margin-right 10px
    }
  }
}

.vat {
  color #4dd385 !important
}

.comment-headline {
  font-size 24px
  display flex
  align-items center
  margin-left 20px
  margin-top 80px
}

.vsys {
  display none !important
}

a {
  color #000
  text-decoration underline
}

.tips {
  margin: 1.5em 1.5em 12px;
  padding: 24px;
  font-size: 14px;
  border-radius: 12px;
  background-color: #F7F7F5;
}
</style>