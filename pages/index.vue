<template>
  <div class="content-container container mx-auto h-screen">
    <!--    Welcome Section start -->
    <div class="intro-container grid grid-cols-1 h-full place-content-center ">

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
            <a  href="#about">
              <p class="intro-nav-item text-gray-800">
                about
              </p>
            </a>
            <a href="#portfolio">
              <p class="intro-nav-item text-gray-800">
                portfolio
              </p>
            </a>
            <a href="#contact">
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
    <div id="about" class="about-section my-24 h-screen mx-auto w-3/5 text-xs sm:text-sm md:text-base">
      <div class="about-section-wrapper h-full flex flex-wrap content-center">
        <div class="about-nav w-full flex">
          <a class="text-gray-800" href="#portfolio">portfolio</a>
          <a class="text-gray-800 mx-5" href="#contact">contact</a>
          <p class="text-right w-full">About</p>
        </div>
        <hr class="my-2 w-full">
        <div class="about-text">
          <div class="about-paragraph-section my-4">
            <p class="text-lg">Who am I exactly?</p>
            <p>That's a good question. I don't know.</p>
          </div>
          <div class="about-paragraph-section">
            <p class="text-lg">What can I do?</p>
            <p>I work with all things related to websites and web development. To me, websites aren’t just a nice
              interface for information, a website can be so much more.</p>
            <p>It is a piece of interactive art, you can make it bend and twirl as you want and it all comes together as
              something useful. </p>
            <p>I create digital art, I very much enjoy the beauty in chaos, dystpoianism, brutalism, all things grunge
              and out of line. </p>
            <p>I also play the guitar and write music.</p>
          </div>
        </div>
      </div>
    </div>
    <!--    About Section End -->

    <!--    Portfolio Section Start -->
    <div id="portfolio" class="portfolio-section my-24 h-screen mx-auto w-3/5 text-xs sm:text-sm md:text-base">
      <div class="portfolio-section-wrapper h-full flex flex-wrap content-center">
        <div class="portfolio-nav w-full flex">
          <a class="text-gray-800" href="#about">about</a>
          <a class="text-gray-800 mx-5" href="#contact">contact</a>
          <p class="text-right w-full">Portfolio</p>
        </div>
        <hr class="my-2 w-full">
        <div class="portfolio-content py-2 px-5">
          <ul>
            <li>
              <p class="title">project 1</p>
                <p class="portfolio-item-description text-xs">the project description</p>
            </li>
            <li>
              <p class="title">Consequuntur</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Consequuntur, fugiat?
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
            <li>
              <p class="title">Adipisicing elit</p>
              <p class="portfolio-item-description text-xs">Lorem ipsum dolor sit amet, consectetur
              </p>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <!--    Portfolio Section End -->

    <!--    Contact Section Start -->
    <div id="contact" class="contact-section my-24 h-screen mx-auto w-3/5 text-xs sm:text-sm md:text-base">
      <div class="contact-section-wrapper h-full flex flex-wrap content-center">
        <div class="contact-nav w-full flex">
          <a class="text-gray-800" href="#about">about</a>
          <a class="text-gray-800 mx-5" href="#portfolio">portfolio</a>
          <p class="text-right w-full">Contact</p>
        </div>
        <hr class="my-2 w-full">
        <div class="contact-text">
          <div class="contact-paragraph-section my-4">
            <p class="text-lg">This is the Contact section</p>
            <p>hello.</p>
          </div>

        </div>

      </div>
    </div>
    <!--    Contact Section End -->

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

    },

  }
</script>


<style lang="scss">
  /* Sample `apply` at-rules with Tailwind CSS
  .container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
  }
  */

  .portfolio-content {

    max-height: 260px;
    overflow-y: scroll;
    width: 100%;
    margin-top: 15px;

    &::-webkit-scrollbar {
      width: 20px;
      border: 1px solid white;
    }

    &::-webkit-scrollbar-thumb {
      border: 1px solid white;
      background-color: #5A5A5A;
    }

    ul {
      list-style: none;
    }

    li {

      margin-bottom: 10px;

      p:before {
        display: inline-block;
        width: 1em;
        margin-left: -1em;
        content: "○";
        color: white;
      }

    }
  }

  .portfolio-item-description {
    position: relative;
    overflow: hidden;

    &:after {
      display: inline-block;
      content: "";
      height: 1px;
      background: white;
      position: absolute;
      width: 100%;
      bottom: 5px;
      margin-left: 5px;
    }
  }

  .about-paragraph-section {
    p {
      margin: 10px 0 10px 0;
    }
  }

  .about-nav, .portfolio-nav, .contact-nav {
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
