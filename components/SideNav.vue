<template>
  <div class="side-nav">
    <button class="side-btn" @click="showSideFunc" id="btn">
      <span class="line"></span>
    </button>
    <div class="side-content" v-if="showSide">
    </div>
    <div :class="[showSide?'side-menu show-side':'side-menu']" id="side-menu">
      <div class="header">
        <div class="top"></div>
        <div class="logo">
          <img src="/logo.jpg" alt="">
        </div>
        <div class="about" @click="showAboutFun">
          svanrj
        </div>
      </div>
      <div class="content">
        <ul>
          <li>
            <ul :class="[showAbout?'about-item show':'hidden']">
              <li><a href="/about">
                <i class="iconfont icon-icon_shouwenmobanguanli"></i>
                关于
              </a></li>
              <li><a href="mailto:kenvinfei@163.com"> <i class="iconfont icon-youxiang"></i>
                邮箱
              </a>
              </li>
              <li><a href="https://github.com/svanrj1219"> <i class="iconfont icon-github"></i>
                Github
              </a>
              </li>
              <li><a href="https://steamcommunity.com/profiles/76561198870747321/"> <i class="iconfont icon-steam"></i>
                Steam
              </a>
              </li>
            </ul>
          </li>
          <li v-for="item in $themeConfig.nav">
            <a :href="item.link"> <i :class="`iconfont ${item.icon}`"></i>
              {{ item.text }}
            </a>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SideNav",
  data() {
    return {
      showAbout: false,
      showSide: false
    }
  },
  methods: {
    //禁止滚动
    stopScroll() {
      const mo = function (e) {
        e.preventDefault();
      };
      document.body.style.overflow = 'hidden';
      document.addEventListener("touchmove", mo, false);//禁止页面滑动
    },
    /***取消滑动限制***/
    canScroll() {
      const mo = function (e) {
        e.preventDefault();
      };
      document.body.style.overflow = '';//出现滚动条
      document.removeEventListener("touchmove", mo, false);
    },
    showAboutFun() {
      this.showAbout = !this.showAbout
    },
    showSideFunc() {
      this.showSide = true
      this.stopScroll()
    }
  },
  mounted() {
    document.addEventListener("click", e => {
      if (document.getElementById("btn").contains(e.target) || document.getElementById("side-menu").contains(e.target)) {
        this.showSide = true
      } else {
        this.showSide = false
        this.canScroll()
      }
    })
  }
}
</script>

<style scoped lang="stylus">
.side-btn {
  background #000
  width 40px
  height 40px
  position fixed
  left 25px
  top 25px
  border-radius 50%
  text-align center
  display flex
  justify-content center
  align-items center
  opacity .8

  .line {
    display block
    width 18px
    border-radius 50px
    background #eeeeee
    height 2px
    position relative
  }

  .line::after, .line::before {
    content ''
    width: inherit;
    height 2px
    display block
    background: #eeeeee;
    position absolute
    border-radius 50px
  }

  .line::after {
    top 5px
  }

  .line::before {
    bottom 5px
  }
}

.side-content {
  height 100vh
  width 100vw
  position fixed
  top 0
  left 0
  background #000
  opacity 0.5
  z-index 10
}


.show-side {
  width 18% !important
  height 100%
  z-index 20
}

.side-menu {
  position fixed
  top 0
  left 0
  width 0
  background white
  height 100%
  overflow auto
  transition width 0.2s ease-in-out

  .header {
    width 100%
    height 160px
    box-sizing border-box
    background url("https://www.wanshouy.cn//1663577564644.gif")
    background-size 100%
    display flex
    flex-direction column
    justify-content space-between
  }

  .content {
    min-height calc(100% -75pt)
  }

  .logo {
    margin-left 15px
    margin-top: 10px;

    img {
      width 55px
      border-radius 50%
    }
  }

  .about {
    box-sizing border-box
    padding 15px 15px
    border-top-left-radius 16px
    border-top-right-radius 16px
    backdrop-filter: blur(4px);
    color #e0e0e0
    width 100%
    background rgba(0, 0, 0, .6)
    display flex
    align-items center
  }

  @keyframes slide-down {
    0% {
      transform: scale(1, 0);
    }
    100% {
      transform: scale(1, 1);
    }
  }

  .show {
    max-height 800px
    transition max-height 0.3s ease-in
    transform-origin 50% 0
    animation slide-down 0.3s ease-in
  }

  .hidden {
    max-height: 0;
    overflow: hidden;
    transition: max-height 1s ease-out;
  }

  ul {
    list-style none
    margin 0
    padding 0
  }

  ul {
    margin 10px 0
    padding 0 16px

    a {
      text-decoration none
      font-weight 600
      display flex
      align-items center
      border-radius 16px
      padding 0 16px
      margin 10px 0
    }

    a:hover {
      background #f1f1f1
    }
  }
}

i {
  font-size 25px
  margin-right: 20px;
  font-weight 200
}

.side-menu::-webkit-scrollbar {
  width: 6px;
}

.side-menu::-webkit-scrollbar-track {
  background-color: black;
}

.side-menu::-webkit-scrollbar-thumb {
  background: #4e4e4e;
  border-radius: 25px;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}

.fade-enter, .fade-leave-active {
  opacity: 0
}
</style>