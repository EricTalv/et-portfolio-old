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
            <a href="#about">
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
      <div class="portfolio-section-wrapper h-full w-full flex flex-row flex-nowrap overflow-x-hidden">
        <div id="portfolio-list" class="portfolio-sec-wrapper min-w-full flex flex-wrap content-center">

          <nuxt-content :document="portfolio"></nuxt-content>


          <div class="portfolio-nav w-full flex">
            <a class="text-gray-800" href="#about">about</a>
            <a class="text-gray-800 mx-5" href="#contact">contact</a>
            <p class="text-right w-full">Portfolio</p>
          </div>
          <hr class="my-2 w-full">


          <div class="portfolio-content py-2 px-10">
            <ul>
              <li v-for="portfolioItem of portfolio" :key="portfolioItem.slug">
                <a @click="setCurrentPortfolioItem(portfolioItem)" :href="`#${portfolioItem.slug}`">

                  <p class="portfolio-item-title">{{ portfolioItem.title }}</p>
                  <p class="portfolio-item-description text-xs">{{ portfolioItem.description }}</p>

                </a>
              </li>
            </ul>
          </div>
        </div>

        <div v-if="currentPortfolioItem" :id="currentPortfolioItem.slug"
             class="portfolio-sec-wrapper min-w-full flex flex-wrap content-center ">
          <div class="portfolio-nav w-full flex">
            <a class="text-gray-800" href="#portfolio-list"><-</a>
            <a class="text-gray-800 mx-5" href="#about">about</a>
            <a class="text-gray-800 " href="#contact">contact</a>
            <p class="text-right w-full">{{ currentPortfolioItem.title }}</p>
          </div>
          <hr class="my-2 w-full">
          <div class="portfolio-content  block sm:flex py-2 px-10">
            <div class="w-48 mx-auto sm:mx-0">
              <img class="w-48 h-48" src="#" alt="">
              <silent-box :gallery="images"></silent-box>

              <a href="#" class="mt-2 float-right">view</a>
            </div>
            <div class="portfolio-item-body mt-10 sm:mt-0 sm:ml-5 text-xs sm:text-sm"
                 v-html="currentPortfolioItem.body">
            </div>
          </div>
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
        <div class="contact-text pt-10 flex mx-auto">
          <div class="py-5 mr-14">
            <div class="text-base ">Email</div>
            <div class="text-sm">eric.talviste@gmail.com</div>

            <div class="my-3">
              <div class="text-base">Phone</div>
              <div class="text-sm">upon request</div>
            </div>

            <div class="text-base ">Location</div>
            <div class="text-sm ">Estonia, Tallinn</div>
          </div>

          <div class="border border-white w-52 h-48 ml-14 flex">
            <div class="m-auto">
              <div>GitHub</div>
              <br>
              <div>LinkedIn</div>
            </div>
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

  data() {
    return {

      images: [
        {
          src: 'images/image001.jpg',
          description: 'Sunken dreams II. by Arbebuk',
        },
        {
          src: 'images/image002.jpg',
          description: 'Tunnel View Sunrise by Porbital',
        }
      ],


      currentPortfolioItem: {},

      portfolio: [
        {
          slug: "my-project",
          title: "My Project",
          description: "This is my project small description",
          body: "This is the body of my project",
          images: [
            {
              src: '~/assets/images/image001.jpeg',
              description: 'The Earth From Space',
            },
            {
              src: '~/assets/images/image002.jpeg',
              description: 'Ready, Set, Launch, Lift off!',
            }
          ]
        },
      ]
    }
  },

  methods: {

    setCurrentPortfolioItem(portfolioItem) {

      this.currentPortfolioItem = portfolioItem;
      console.log(this.currentPortfolioItem);
    }

  },

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

.portfolio-section-wrapper, {
  scroll-behavior: smooth;
}

.portfolio-content {

  max-height: 260px;
  overflow-y: auto;
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

    margin-bottom: 25px;

    transition: all .5s;

    &:hover {
      margin-left: 10px;
    }

    p:before {
      display: inline-block;
      width: 1em;
      margin-left: -1em;
      content: "○";
      color: white;

    }

    p {
      &:hover {
        &:before {
          content: "⦿";
        }
      }
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
