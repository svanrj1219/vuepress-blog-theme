<template>
  <div class="aside-content">
    <div class="card-widget">
      <div class="card-content">
        <div class="card-info-avatar">
          <div class="author-info__sahib">👋 {{ getTimeState }}！</div>
        </div>
        <div class="amos-card-content">
          <div class="amos-hello">
            我是 <span class="amos-hello-strong">svanrj</span>
            <br><br>
            在这块小地方记录自己，
            <br>
            关于技术、生活、分享的片段，
            <br>
            如果感兴趣的话，
            <br>
            欢迎 👇
            <br>

          </div>
          <div>
            <a href="/about">
              <button class="amos-btn">关于 / 留言</button>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  computed: {
    tags() {
      return this.$tag.list
    },
    archiveList() {
      let res = {};
      let tmp = [];
      let list = this.$site.pages.filter((item) => {
        return item.pid === "post";
      });
      list.map((item) => {
        const date = new Date(item.frontmatter.date);
        const year = date.getFullYear();
        const month = date.getMonth();
        const day = `${date.getDate()}`;
        res[year] || (res[year] = []);
        item.date = `${`${month + 1}`.padStart(2, 0)}-${day.padStart(2, 0)}`;
        res[year].push(item);
      });
      for (let [key, item] of Object.entries(res)) {
        tmp.push({
          year: +key,
          total: item.length,
        });
      }
      tmp.sort((a, b) => {
        return b.year - a.year;
      });
      return tmp;
    },
    getTimeState() {
      // 获取当前时间
      let timeNow = new Date();
      // 获取当前小时
      let hours = timeNow.getHours();
      // 设置默认文字
      let text = ``;
      // 判断当前时间段
      if (hours >= 0 && hours <= 10) {
        text = `早上好`;
      } else if (hours > 10 && hours <= 14) {
        text = `中午好`;
      } else if (hours > 14 && hours <= 18) {
        text = `下午好`;
      } else if (hours > 18 && hours <= 24) {
        text = `晚上好`;
      }
      return text;
    }
  }
}
</script>

<style lang="stylus" scoped>

.aside-content {
  padding-left: 1rem;
  width: 280px;

  .card-widget {
    background: linear-gradient(-225deg, #1d1c24, #4b3c41);
    background-size: 100%;
    box-shadow: 0 0 12px 4px rgba(0, 0, 0, .05);
    animation: gradient 15s ease infinite;
    position: relative;
    border-radius: 12px;
    padding 58px 25px


    &:first-child {
      margin-top: 0;
      transition: .3s;
    }
  }

  .author-info__sahib {
    color: #ffffff;
    font-weight: 800;
  }

  .amos-hello {
    margin 3px 0
  }

  .amos-hello-strong {
    color #ffffff
    font-size 14px
    font-weight 600
  }

  .amos-card-content {
    font-size: 14px;
    font-weight: 600;
    color: #adaab2;
    line-height: 26px;
  }
  .amos-btn{
    position: relative;
    left: -4px;
    cursor: pointer;
    outline: none;
    height: 40px;
    padding: 0 32px;
    margin-top: 18px;
    font-family: inherit;
    font-size: 14px;
    font-weight: 600;
    color: #fff;
    background-color: #000000;
    border: none;
    border-radius: 12px;
    text-shadow: 0 -1px 0 rgba(0,0,0,.12);
    box-shadow: 0 2px 0 rgba(0,0,0,.045);
    transition: all .3s cubic-bezier(.645,.045,.355,1);
  }
.amos-btn:hover{
  color:#9a989b;
}
}
</style>