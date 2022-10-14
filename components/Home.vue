<template>
  <div>
    <main
        class="home"
    >
      <div class="content">
        <handers/>
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
  name: 'Home',
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
.home
  display flex
  justify-content center
</style>
