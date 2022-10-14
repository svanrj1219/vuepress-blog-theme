<template>
  <div class="post">
    <div class="article">
      <div v-for="(item,idx) in $pagination.pages" :key="idx" class="article-item">
        <div class="post_cover right_radius">
          <router-link :to="item.path" :title="item.frontmatter.title">
            <img class="post_bg" :src="item.frontmatter.cover" :alt="item.frontmatter.title">
          </router-link>
        </div>
        <div class="recent-post-info-top">
          <router-link class="article-title" :to="item.path">
            {{ item.frontmatter.title }}
          </router-link>
        </div>
        <div class="post-content">
          {{ item.frontmatter.abstract }}
          <p>
            <router-link :to="item.path" :title="item.frontmatter.title">
              阅读全文
            </router-link>
          </p>
        </div>
        <div class="recent-post-info">
          <div class="user-info">
            <img src="/logo.jpg" alt="svanrj">
            <div class="info">
              <span class="name">{{ item.frontmatter.author }}</span>
              <span class="date">{{ item.timeAgo }}</span>
            </div>
          </div>
          <div class="categories" v-if="item.frontmatter.category">
            <router-link class="article-meta__categories" :to="`/categories/${item.frontmatter.category}/`">
              {{ getCategoryText(item.frontmatter.category) }}
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: "Post",
  methods: {
    goPage(path) {
      this.$router.push({
        path
      })
    },
    getCategoryText(link) {
      return this.$site.themeConfig.category.filter(e => e.link === link)[0]['text']
    }
  },
  mounted() {
    console.log(this.$pagination)
  }
}
</script>

<style scoped lang="stylus">
.post
  width: 900px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;

  .article-item
    width 900px
    height 602px
    margin-bottom 40px
    background #ffffff
    border-radius 20px

    .post_cover
      height 320px

    .post_bg
      width 100%
      height 320px
      border-radius 20px 20px 0 0
      object-fit cover

    .recent-post-info-top
      font-size: 22px;
      margin: 20px;

      .article-title
        font-family: 'Fedra Sans', sans-serif;
        color #31353a
        line-height 40px;
        font-weight 600;
        text-decoration none

    .post-content
      font-size 14px
      color: #31353a;
      font-weight: 600;
      line-height: 1.7;
      letter-spacing: 1px;
      padding-left 20px
      height 95px

      a
        color: #31353a;
        text-decoration underline
        font-weight: 600;
        font-size 14px

  .recent-post-info
    display flex
    justify-content space-between
    align-items center
    padding 40px 10px 0px 10px


    .user-info
      display flex
      align-items center
      color: #31353a !important;

      img
        height 35px
        width 35px

      .info
        display flex
        flex-direction column
        margin-left 10px
        justify-content center

        .name
          font-size 14px
          font-weight 600

        .date
          font-size 14px


    .categories
      display inline-block
      text-decoration: none
      font-weight: 400
      font-size: 12px
      color: #000000
      background: #F6F9FD
      padding: 6px 10px
      border-radius: 6px
      margin-right 10px
      height 20px

      a
        color #31353a
        font-weight 400
        text-decoration none


</style>