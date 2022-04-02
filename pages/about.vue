<template>
  <main class="about_container">

    <div class="nav">
      <a class="nav--item" href="/design">design</a>
      <a class="nav--item" href="/development">dev</a>
    </div>

    <div class="about_body_wrapper">

      <h1 class="about_title">ABOUT</h1>

      <div class="about_body">
        <div class="text_group">
          <div class="text_group--title">Who am I</div>
          <div class="text_group--description">graphic design and web enthusiast</div>
        </div>
        <div class="text_group">
          <div class="text_group--title">Contact</div>
          <div class="text_group--description">eric@erictalviste.com</div>
        </div>
        <div class="link_group">
          <a target="_blank" href="https://www.behance.net/erictalviste6">
            <img src="../assets/images/social-icons/behance.svg" alt="">
          </a>
          <a target="_blank" href="https://dribbble.com/EricTalv">
            <img src="../assets/images/social-icons/dribbble.svg" alt="">
          </a>
          <a target="_blank" href="https://www.instagram.com/et_experience/">
            <img src="../assets/images/social-icons/instagram.svg" alt="">
          </a>
          <a target="_blank" href="https://github.com/EricTalv">
            <img src="../assets/images/social-icons/github.svg" alt="">
          </a>
          <a target="_blank" href="https://www.linkedin.com/in/erictalviste/">
            <img src="../assets/images/social-icons/linkedin.svg" alt="">
          </a>

        </div>
      </div>



    </div>

    <div class="about-sidebar"></div>
  </main>
</template>

<script>
export default {
  name: "about"
}
</script>

<style lang="scss" scoped>
/* BreakPoints */
$breakpoint-tablet: 768px;
$breakpoint-mobile: 501px;



// ====  ON MOBILE
.about_container {
  width: 100%;

  background-color: black;
  background-image: url("../assets/images/about-bg-main.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;


  // TEXT ========= MOBILE
  .about_body, .about_title, .nav {
    color: white;
    font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
    text-shadow: 0px 0px 10px #000000;
  }

  .about_title {
    text-align: center;
    font-size: 4em;
  }

  .about_body {
    text-align: center;
    font-size: 1.2em;
    font-family: 'IBM Plex Mono', monospace;

    .text_group {
      margin: 50px 0;
    }

    .text_group--title {
      text-decoration: underline;
      margin-bottom: 10px;
    }

    .link_group {
      display: flex;
      justify-content: center;


      a {

        transition: all .5s;


        &:hover {
          opacity: .5;
        }
      }

    }

  }

  .nav {

    width: 100%;

    position: absolute;
    padding: 20px;

    display: flex;

    justify-content: space-around;

    .nav--item {
      font-size: 1.5em;

      transition: all .5s;

      &:hover {
        letter-spacing: 5px;
      }
    }
  }

  .about_body_wrapper {
    height: 100%;
    display: flex;
    flex-flow: column;
    justify-content: center;
  }



}




// ====  Index media queries - ON TABLET
@media  (min-width: $breakpoint-mobile) {

}

// ====  Index media queries - ON DESKTOP
@media  (min-width: $breakpoint-tablet) {

}
</style>
