<template>
  <div class="back-to-top" v-show="visible">
    <button href="" class="toTop" @click="backToTop">
      <img src="https://amoshk.top/img/icon/blog_top-i.svg" alt="">
    </button>
  </div>
</template>

<script>
export default {
  name: "BackTop",
  data() {
    return {
      visible: false,
      interval: null,
      isMoving: false,
    }
  },
  methods: {
    handleScroll() {
      this.visible = window.scrollY > 400;
    },
    backToTop() {
      if (this.isMoving) return;
      const start = window.scrollY;
      let i = 0;
      this.isMoving = true;
      this.interval = setInterval(() => {
        const next = Math.floor(-window.scrollY / 5) + window.scrollY;
        if (next <= 5) {
          window.scrollTo(0, 5);
          clearInterval(this.interval);
          this.isMoving = false;
        } else {
          window.scrollTo(0, next);
        }
        i++;
      }, 16.7);
    },
    easeInOutQuad(t, b, c, d) {
      if ((t /= d / 2) < 1) return (c / 2) * t * t + b;
      return (-c / 2) * (--t * (t - 2) - 1) + b;
    },
  },
  mounted() {
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener("scroll", this.handleScroll);
    if (this.interval) {
      clearInterval(this.interval);
    }
  },
}
</script>

<style scoped lang="stylus">
.toTop {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  text-align: center;
  color: #fff;
  background: #000;
  cursor: pointer;
  -webkit-transition: all .1s ease-out;
  transition: all .1s ease-out;
  position: fixed;
  bottom 20px
  right 25px
  overflow: hidden;
  display flex
  align-items center
  justify-content center
}

</style>