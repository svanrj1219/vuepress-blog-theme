<template>
  <div>
    <main
        class="posts"
    >
      <div class="content">
        <post/>
      </div>
      <side-bar/>
    </main>
  </div>

</template>

<script>
import Post from "./Post"
import sideBar from "./sideBar"
import Handers from "./Hander"

export default {
  name: 'Posts',
  components: {
    Post, sideBar, Handers
  },


  computed: {
    data() {
    },
  }
}
</script>

<style lang="stylus">
.posts {
  display flex
  justify-content center
}
</style>
