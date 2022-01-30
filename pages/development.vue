<template>
  <main class="dev-container">
      <div class="dev-title">
        DEVELOPMENT
      </div>
      <div class="dev-list">

        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>
        <a href="#" class="dev-item">This Portfolio</a>

      </div>

      <div class="dev-nav">
        <a href="" class="dev-nav__item">about</a>
        <a href="" class="dev-nav__item">design</a>
      </div>
  </main>
</template>

<script>
export default {
name: "development"
}
</script>

<style lang="scss" scoped>


  // ====  ON MOBILE
  // =  Dev Background
  .dev-container {
    width: 100%;

    background-color: black;
    background-image: url("../assets/images/mobile-bg.png");
    background-repeat: no-repeat;
    background-position: center;

    background-size: 100% 1500px;
  }

  // =  Dev Text Defaults
  .dev-item, .dev-title, .dev-nav__item {
    color: white;
    font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
    text-shadow: 0px 0px 10px #000000;
  }

  .dev-title {
    font-size: 4em;
    padding: 20px 0 20px 0;
    width: 100%;
    text-align: center;
  }

  // =  Dev List
  .dev-list {
    width: 100%;
    height: 70vh;

    overflow-y: auto;


  }

  // =  Dev List Item
  .dev-item {
    background-image: url("../assets/images/dev-item-mobile-bg.png");
    background-repeat: no-repeat;
    background-size: cover;

    color: white;
    display: block;

    padding: 50px;

    text-align: center;

    font-size: 1.5em;

    margin-bottom: 20px;

    &:last-child {
      margin-bottom: 0;
    }
  }

  // =  Dev Nav
  .dev-nav {
    display: flex;
    justify-content: space-around;
    align-items: center;

    bottom: 50px;
    left: 50%;
    transform: translateX(-50%);
    position: fixed;

    .dev-nav__item {
      font-size: 2.5em;
      margin: 0 60px 0 60px;
    }
  }



  /* BreakPoints */
  $breakpoint-tablet: 768px;
  $breakpoint-mobile: 501px;
</style>
