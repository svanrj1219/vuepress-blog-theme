<template>
  <div>
    <main id="content-inner" class="main">
      <div id="post" class="post">
        <div class="head">
          <img :src="this.$page.frontmatter.cover" alt="">
          <div class="title">
            {{ this.$page.frontmatter.title }}
          </div>
          <div class="info">
            <div class="user-info">
              <img id="logo" src="/logo.jpg" alt="svanrj">
              <div class="a-info">
                <span class="name">{{ this.$page.frontmatter.author }}</span>
                <span class="date">发布时间:{{ this.$page.timeAgo }}</span>
              </div>
            </div>
            <div class="opt">
              <div class="tag opt-item" id="tag" v-if="this.$page.frontmatter.category" @click="showTag">
                <img src="/tag.png" alt="">
              </div>
              <div class="share opt-item">
                <img src="/share.png" alt="">
              </div>
              <div class="tag-content" v-if="tagIsShow">
                <div class="tag-item" v-for="item in $page.frontmatter.tags">
                  <router-link :to="`/tags/${item}`">
                    {{ item }}
                  </router-link>
                </div>
              </div>
            </div>
          </div>
        </div>
        <div class="warp">
          <article id="article-container">
            <Content class="vp-doc"/>
          </article>
        </div>
        <blockquote>
          <p>
            转载请遵循 <a href="https://creativecommons.org/licenses/by-nc-sa/4.0/deed.zh" target="_blank"><img
              src="https://i.creativecommons.org/l/by-nc-sa/4.0/80x15.png" style="width: 86px;border-radius: 0px;"></a>
            协议许可<br>本文所有内容严禁任何形式的盗用
          <div class="author">
          <span>

            本文作者：Svanrj
          </span>
            <span id="author-avatar"> &nbsp
          <img src="/logo.jpg" width="20px" height="20px" style="border-radius: 50%" alt="Amos"/>
          </span>
          </div>
          本文链接：<a href="#" @click="()=>{
              this.$router.push(this.$page.path)
            }">www.wanshouy.cn{{ this.$route.path }}</a>
        </blockquote>
        <valine/>
      </div>
    </main>
    <postnav/>
  </div>
</template>

<script>
import valine from "./Valine";
import postnav from "./Postnav";

export default {
  components: {
    valine, postnav
  },
  data() {
    return {
      tagIsShow: false
    }
  },
  methods: {
    showTag() {
      this.tagIsShow = true;
    },
  },
  mounted() {
    document.addEventListener("click", e => {
      this.tagIsShow = document.getElementById("tag").contains(e.target);
    })
  },
}

</script>

<style lang="stylus" scoped>
#content-inner {
  max-width: 1000px;
  display: flex;
  justify-content: space-between;
  padding: 1rem 2rem;
  margin: 0 auto;

  #post {
    box-shadow: 0 8px 16px -4px #00000050;
    border-radius: 12px;
    background: #ffffff;
    width: 100%;

    .head {
      img {
        width 100%
        height 320px
        object-fit cover
        border-radius 15px 15px 0 0
      }

      .title {
        font-size 23px
        text-align center
        font-family: 'Fedra Sans', sans-serif;
        color #31353a
        font-weight 600;
        margin: 48px 18px 48px 18px;
      }
    }

    .warp {
      padding: 1rem 2rem;
    }
  }

  .user-info {
    display flex
    align-items center
    color: #31353a !important;
  }

  #logo {
    height 35px !important
    width 35px !important
  }

  .a-info {
    display flex
    flex-direction column
    margin-left 5px
  }

  .info {
    padding 0 20px
    align-items center
    display flex
    margin-left 10px
    justify-content space-between
  }

  .name {
    font-size 14px
    font-weight 600
  }

  .date {
    padding 3px 0
    font-size: 12px;
    font-weight: 400;
    color: #74858F;
  }

  .opt {
    display flex
    align-items center
    position relative
    box-sizing border-box

    .opt-item {
      padding 5px
      border-radius 50%
      width 23px
      height 23px
      display flex
      align-items center
      justify-content center

      img {
        width 23px !important
        height 23px !important
      }
    }

    .opt-item:hover {
      background #ededed

    }
  }

  blockquote {
    font-size: 1em;
    padding: 0.5em 1em;
    border-left: 3px solid #ff7875;
    background-color: #F5F5F5;
    list-style: none;
    margin 20px 0px 20px 50px
    width 80%

    p {
      line-height 30px
      font-size 14px
    }

    a {
      color #000
      text-decoration underline
    }
  }

  .author {
    display flex
    align-items stretch
  }
}


.tag-content {
  background #fff
  width 110px
  overflow visible
  max-height 210px
  position absolute
  box-sizing border-box
  top 30px
  right 40px
  border-radius: 10px;
  box-shadow: 0 0 30px 0 rgba(43, 86, 112, .1);
  text-align center
  transform scale(1)
  animation: 3s ease-in 1s;
  z-index 999
}

.tag-item {
  padding 15px 0
  a{
    color #31353a
    text-decoration none
    font-weight 600
  }
}

.tag-item:hover {
  background #eeeeee
}
.tag-item:first-child{
  border-radius10px 10px

}
.tag-item:last-child{
  border-radius 0 0 10px 10px
}
</style>