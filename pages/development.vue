<template>
  <main class="dev-container">
      <div class="title">
        DEVELOPMENT
      </div>
      <div class="dev-list-container">
        <div class="dev-item">
          <div class="dev-item__title">This Portfolio</div>
        </div>
        <div class="dev-item">
          <div class="dev-item__title">This Portfolio</div>
        </div>
        <div class="dev-item">
          <div class="dev-item__title">This Portfolio</div>
        </div>
      </div>
  </main>
</template>

<script>
export default {
name: "development"
}
</script>

<style lang="scss" scoped>

  // ====  Dev Background
  // ====  ON MOBILE
  .dev-container {

    width: 100%;

    background-color: black;
    background-image: url("../assets/images/mobile-bg.png");
    background-repeat: no-repeat;
    background-position: center;

    background-size: 100% 1500px;

  }

  .dev-item, .title {
    color: white;
    font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
    text-shadow: 0px 8px 6px rgba(0,0,0,0.3);
  }

  .title {
    font-size: 4em;
    padding: 20px 0 20px 0;
    width: 100%;
    text-align: center;
  }

  .dev-item {
    background-image: url("../assets/images/dev-item-mobile-bg.png");
    background-repeat: no-repeat;
    background-size: cover;


    margin: 0 0 20px;

    padding: 50px;

    .dev-item__title {
      width: 100%;
      text-align: center;
      font-size: 2em;

    }
  }

  /* BreakPoints */
  $breakpoint-tablet: 768px;
  $breakpoint-mobile: 501px;
</style>
