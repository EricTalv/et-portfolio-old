<template>
  <main class="index">
    <div class="wrapper">
      <div class="title">
        <span class="title--eric">eric</span>
        <span class="title--talv">talviste</span>
      </div>
      <div class="nav">
        <a href="" class="nav__item nav__item--about">about</a>
        <a href="" class="nav__item nav__item--design">design</a>
        <a href="" class="nav__item nav__item--dev">development</a>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  name: "real-index"
}
</script>

<style lang="scss" scoped>

  // ====  Index Background
  // ====  ON MOBILE
  .index {

    width: 100%;

    background-color: black;
    background-image: url("./assets/images/index-mobile-bg.png");
    background-repeat: no-repeat;
    background-position: center;

    background-size: 100% 1500px;

  }

  .wrapper {

    height: 100%;

    display: flex;
    justify-content: center;
    align-content: center;
    flex-flow: column;
  }

  // ====  Index Title
  .title {
    color: white;

    display: flex;
    flex-flow: column;
    align-items: center;

    .title--eric, .title--talv {
      text-transform: uppercase;
    }

    .title--eric {
      font-size: 9em;
      height: 150px;

    }
    .title--talv {
      font-size: 4.3em;
    }
  }

  // ====  Index Nav

  .nav {

    color: white;

    display: flex;
    flex-flow: column;

    text-align: center;


    a {
      font-size: 2.5em;
      margin-bottom: 10px;
    }
  }

  /* BreakPoints */
  $breakpoint-tablet: 768px;
  $breakpoint-mobile: 501px;

  // ====  Index media queries - ON DESKTOP
  @media  (min-width: $breakpoint-mobile) {
    .index {
      background-image: url("./assets/images/index-bg.png");
      background-size: cover;
    }

    .wrapper {

      height: 85%;

      flex-flow: row;
      align-items: center;
    }

    .title, .nav {
      width: 50%;
    }

    .title {

      align-items: end;

      .title--eric, .title--talv {
        font-size: 3.3em;
      }

      .title--eric {
        height: 55px;
      }

    }

    .nav {
      align-items: start;
    }



  }





</style>
