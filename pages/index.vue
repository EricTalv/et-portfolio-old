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

          <div class="portfolio-nav w-full flex">
            <a class="text-gray-800" href="#about">about</a>
            <a class="text-gray-800 mx-5" href="#contact">contact</a>
            <p class="text-right w-full">Portfolio</p>
          </div>
          <hr class="my-2 w-full">

          <div class="portfolio-content py-2 px-3 sm:px-10">

            <ul class="portfolio-unordered-list">

              <li class="portfolio-item" v-for="portfolioItem of portfolio" :key="portfolioItem.slug">
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
          <div v-if="currentPortfolioItem" class="min-w-full">
            <div class="portfolio-nav w-full flex">
              <a class="text-gray-800" href="#portfolio-list"><-</a>
              <a class="text-gray-800 mx-5" href="#about">about</a>
              <a class="text-gray-800 " href="#contact">contact</a>
              <p class="text-right w-full">{{ currentPortfolioItem.title }}</p>
            </div>
            <hr class="my-2 w-full">
            <div class="portfolio-content w-full block sm:flex py-2 px-10">
              <div class="w-48 mx-auto sm:mx-0">
                <silent-box class="mb-3 w-40 h-40 border border-white" :gallery="currentPortfolioItem.images"></silent-box>

                <a v-if="currentPortfolioItem.code" :href="currentPortfolioItem.code " target="_blank" class="sm:float-right text-sm">code</a>
                <a v-if="currentPortfolioItem.link" :href="currentPortfolioItem.link" target="_blank" class="mr-2 sm:float-right text-sm">view</a>

                <hr class="w-40 my-3 sm:hidden">

              </div>



                <div class="portfolio-item-body  sm:mt-0 sm:ml-5 text-xs sm:text-sm"
                     v-html="currentPortfolioItem.body"> </div>

            </div>
          </div>
        </div>
      </div>
    </div>
    <!--    Portfolio Section End -->

    <!--    Contact Section Start -->
    <div id="contact" class="contact-section my-24 h-screen mx-auto w-3/5  text-xs sm:text-sm md:text-base">
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

          <div class="border border-white w-52 h-48 ml-14  hidden sm:flex">
            <div class="m-auto">
              <a href="https://github.com/EricTalv" target="_blank">GitHub</a>
              <br>
              <br>
              <a href="https://www.linkedin.com/feed/" target="_blank">LinkedIn</a>
              <br>
              <br>
              <a href="https://www.instagram.com/et_experience/" target="_blank">Design</a>
            </div>
          </div>
        </div>

        <hr class="w-full mb-2 sm:hidden">

        <div class="flex justify-between w-full sm:hidden">
            <a href="https://github.com/EricTalv" target="_blank">GitHub</a>
            <br>
            <a href="https://www.linkedin.com/in/erictalviste/" target="_blank">LinkedIn</a>
            <br>
            <a href="https://www.instagram.com/et_experience/" target="_blank">Design</a>
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


      currentPortfolioItem: null,



      portfolio: [
        {
          slug: "my-portfolio-old",
          title: "My Portfolio",
          description: "how this portfolio-old was made",
          code: "https://github.com/EricTalv/et-portfolio",
          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('~/assets/images/image001.jpg') ,
              description: 'The Power In My H~ands',
            },
          ]
        },
      ]
    }
  },

  methods: {

    setCurrentPortfolioItem(portfolioItem) {

      this.currentPortfolioItem = portfolioItem;
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

.portfolio-item-body {
  p {
    margin: 10px 0;
  }

  hr {
    margin: 15px 0;
  }

  h3 {
    font-weight: bolder;
  }

  ul {
    list-style: circle;
  }
}

#silentbox-gallery {
  .silentbox-item {
    filter: grayscale(100%);

    transition: filter .5s;

    &:nth-child(n+2) {
      display: none;
    }

    &:hover {
      filter: none;
    }
  }
}

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

  scrollbar-color: #5A5A5A transparent;

  .portfolio-unordered-list {
    list-style: none;
  }

  .portfolio-item {

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
