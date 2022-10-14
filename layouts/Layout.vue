<template>
  <div class="theme-container" >
    <Home v-if="$page.pageType === 'home'"/>
    <!--    <Archive v-else-if="$page.pageType === 'archive'"/>-->
    <!--    <Category v-else-if="$page.pageType === 'category'"/>-->
    <!--    <CategoryItem v-else-if="$page.pageType === 'categoryItem'"/>-->
    <!--    <Tag v-else-if="$page.pageType === 'tag'"/>-->
    <!--    <TagItem v-else-if="$page.pageType === 'tagItem'"/>-->
    <!--    <Link v-else-if="$page.pageType === 'link'"/>-->
    <Articles v-else/>
    <BackTop/>
    <sideNav/>
  </div>
</template>

<script>
import Home from "../components/Home";
import Posts from "../components/Posts";
import Articles from '../components/Articles'
import BackTop from "../components/BackTop";
import sideNav from "../components/SideNav";
// import Category from '../components/Category'
// import CategoryItem from '../components/CategoryItem'
// import Tag from '../components/Tag'
// import TagItem from '../components/TagItem'
// import Post from "../components/Post";
// import Link from "../components/Link";

export default {
  name: "Layout.vue",
  data() {
    return {
      iconIs: false,
    }
  },
  components: {
    Home,
    Articles,
    BackTop,
    sideNav,
    // Archive,
    // Category,
    // CategoryItem,
    // Tag,
    // TagItem,
    Posts,
    // Link
  },
  async mounted() {
  },
}
</script>

<style lang="stylus">
.theme-container
  height 100vh
  padding-top 164px
  background #edeff3
</style>