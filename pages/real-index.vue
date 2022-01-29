<template>
  <main class="index-container">
    <div class="wrapper">
      <div class="title">
        <span class="title--eric">ERIC</span>
        <span class="title--talv">TALVISTE</span>
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


  /* BreakPoints */
  $breakpoint-tablet: 768px;
  $breakpoint-mobile: 501px;

  // ====  Index Background
  // ====  ON MOBILE
  .index-container {

    width: 100%;

    background-color: black;
    background-image: url("../assets/images/mobile-bg.png");
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

  // ==== Index Text Styles
  .title, .nav {
    text-shadow: 0px 8px 6px rgba(0,0,0,0.3);
    font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
  }

  // ====  Index Title
  .title {

    color: white;

    display: flex;
    flex-flow: column;
    align-items: center;


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


    .nav__item {
      font-size: 2.5em;
      margin-bottom: 10px;

      transition: .5s all;
      // ==== Index Nav item hovers
      &:hover {
        letter-spacing: 5px;
      }
    }
  }

  // ====  Index media queries - ON TABLET
  @media  (min-width: $breakpoint-mobile) {
    .index {
      background-image: url("../assets/images/big-bg.png");
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

    // ====  Index Title
    .title {
      align-items: end;
      margin-right: 10px;

      .title--eric, .title--talv {
        font-size: 3.3em;
      }

      .title--eric {
        height: 55px;
      }

    }

    // ====  Index Nav
    .nav {
      align-items: start;

      margin-left: 10px;

      .nav__item {
        font-size: 2em;
      }
    }

    // ====  Index media queries - ON DESKTOP
    @media  (min-width: $breakpoint-tablet) {
      // ====  Index Title
      .title {

        margin-right: 25px;

        .title--eric, .title--talv {
          font-size: 7vw;
        }

        .title--eric {
          height: 6.5vw;
        }
      }

      // ====  Index Nav
      .nav {
        margin-left: 25px;

        .nav__item {
          font-size: 3vw;
        }
      }
    }

  }

</style>
