<template>
  <div class="post-operate">

    <router-link v-if="$mkPrevPageItem" class="post-operate__prev" :to="$mkPrevPageItem.path">
            <i class="iconfont icon-arrow-back"></i>
      <span>
      {{ $mkPrevPageItem.title }}
        </span>
    </router-link>
    <router-link v-if="$mkNextPageItem" class="post-operate__next" :to="$mkNextPageItem.path">
      {{ $mkNextPageItem.title }}
      <i class="iconfont  icon-arrow-back-copy"></i>
    </router-link>
  </div>
</template>
<script>
import mixins from '../mixins/index';

export default {
  name: 'PostNav',
  mixins: [mixins]
}
</script>
<style lang="stylus">
.post-operate
  margin auto
  width 1000px
  display: flex;
  padding: 1.5rem 0;

  a {
    width 100%
    text-decoration none
    font-weight 400
    color #333
    display flex
    align-items center
  }

  .post-operate__next {
    justify-content right
  }
  i {
    font-size 30px
    background #ffffff
    border-radius 50%
    margin 0 10px
  }
</style>