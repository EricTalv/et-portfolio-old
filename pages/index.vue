<template>
  <div class="content-container container mx-auto h-screen">
    <!--    Welcome Section start -->
    <div class="intro-container">

      <sphere></sphere>
      <div class="flex flex-col items-center">
        <div class="p-7 text-xs sm:text-sm md:text-base">
          <small class="intro-text text-gray-600">
            <p>
              Estonia, Tallinn
            </p>
          </small>
          <p class="intro-text">
            I am Eric Talviste.
          </p>
          <p class="intro-text">
            I develop websites, music and create digital art.
          </p>
          <hr class="my-3">
          <div class="intro-nav flex justify-between">
            <a href="">
              <p class="intro-nav-item text-gray-800">
                portfolio
              </p>
            </a>
            <a href="">
              <p class="intro-nav-item text-gray-800">
                about
              </p>
            </a>
            <a href="">
              <p class="intro-nav-item text-gray-800">
                contact
              </p>
            </a>
          </div>
        </div>
      </div>
    </div>
    <!--    Welcome Section End -->

    <!--    About Section Start -->
    <div class="about-section h-screen my-auto mx-auto w-3/5 text-xs sm:text-sm md:text-base">
      <div class="about-nav flex">
        <a class="text-gray-800" href="">portfolio</a>
        <a class="text-gray-800 mx-5" href="">contact</a>
        <p class="text-right w-full">About</p>
      </div>
      <hr class="my-2">
      <div class="about-text">
        <div class="about-paragraph-section my-4">
          <p class="text-lg">Who am I exactly?</p>
          <p>That's a good question. I don't know.</p>
        </div>
        <div class="about-paragraph-section">
          <p class="text-lg">What can I do?</p>
          <p>I work with all things related to websites and web development. To me, websites aren’t just a nice interface for information,  a website can be so much more.</p>
          <p>It is a piece of interactive art, you can make it bend and twirl as you want and it all comes together as something useful. </p>
          <p>I create digital art, I very much enjoy the beauty in chaos, dystpoianism, brutalism, all things grunge and out of line. </p>
          <p>I also play the guitar and write music.</p>
        </div>

      </div>
    </div>
    <!--    About Section End -->

  </div>
</template>

<script>

  import baffle from 'baffle';

  export default {

    mounted() {

      // Baffle Animation
      let introText = baffle('.intro-text');
      introText.reveal(1000);

      let navItem = baffle('.intro-nav-item');
      navItem.reveal(3500);

    }

  }
</script>


<style lang="scss">
  /* Sample `apply` at-rules with Tailwind CSS
  .container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
  }
  */

  .about-paragraph-section {
    p {
      margin: 10px 0 10px 0;
    }
  }

  .about-nav {
    a {
      transition: color .5s;

      &:hover {
        color: white;
      }
    }
  }

  .intro-nav {
    a {
      p {
        transition: all .5s;

        &:hover {
          color: white;
        }
      }
    }
  }

</style>
