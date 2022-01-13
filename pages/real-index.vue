<template>
  <main class="index">
    <div class="index__left-panel"></div>
    <div class="index__right-panel"></div>
  </main>
</template>

<script>
export default {
  name: "real-index"
}
</script>

<style lang="scss" scoped>

  //  Index background
  .index {

    width: 100%;

    background-color: black;
    background-image: url("./assets/images/index-mobile-bg.png");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;

  }

  /* BreakPoints */
  $breakpoint-tablet: 768px;
  $breakpoint-mobile: 501px;

  // Index Background media queries
  @media  (min-width: $breakpoint-mobile) {
    .index {
      background-image: url("./assets/images/index-bg.png");

    }
  }




</style>
