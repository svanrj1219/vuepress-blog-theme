<template>
  <div class="hander">
    <div class="mdl-card">
      <div class="mdl-card__media"
           style="background-image:url(/1663577564644.gif)">
        <p class="index-top-block-slogan"><a href="/about">
          👀
        </a></p>
      </div>
    </div>
    <div class="my-card">
      <div></div>
      <div class="logo">
        <img src="/logo.jpg" alt="">
      </div>
      <div class="about">
        <div class="name">svanrj</div>
        <div class="fun">
          <span class="fun-icon">
            <img src="/fun.png" alt="">
          </span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Hander"
}
</script>

<style scoped lang="stylus">
.hander {
  max-width: 900px;
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  margin-bottom: 20px;
}

.mdl-card {
  width: 64%;
}

.mdl-card__media {
  min-height: 360px;
  background-position: cover;
  background-repeat: no-repeat;
  background-size: 100% 100%;
  border-radius: 20px;
  display: flex;
  align-items: flex-end;
  padding-left: 20px;
  font-size: 25px;

  p {
    margin: 10px 0;
  }

}

.my-card {
  background: #fff;
  border-radius: 20px;
  width: 28%;
  padding: 20px;
  display: flex;
  justify-content: space-between;
  flex-direction: column;

  .logo {
    text-align: center;

    img {
      width: 150px;
      height: 150px;
    }

  }

  .about {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .fun-icon {

    img {
      width: 25px;
      opacity: .8;
    }

  }
}
</style>