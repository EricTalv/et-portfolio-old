<template>
  <!--    Dev Portfolio Section Start -->

  <div class="about-section flex flex-wrap  justify-center">
    <div class="about-wrapper mt-44 w-3/5 c-min-width">
      <div class="about-nav w-full flex">

        <div class="flex items-end">
          <a href="#">about</a>
          <a class="mx-3" href="#">contact</a>
        </div>

        <div class="w-full text-right flex flex-col">
          <p class="">Portfolio</p>
          <div class="flex justify-end">
            <p>development</p>
            <p>/Design</p>
          </div>
        </div>


      </div>

      <hr class="my-2 ">

      <div id="dev-portfolio-list" class="portfolio-container flex mx-auto justify-center flex-col">
        <div id="portfolio-list" >
          <div class="portfolio-list-body ">
            <ul class="portfolio-unordered-list">
              <li class="portfolio-item" v-for="portfolioItem of portfolio" :key="portfolioItem.slug">
                <a @click="setCurrentPortfolioItem(portfolioItem)" :href="`#${portfolioItem.slug}`">
                  <p class="portfolio-item-title">{{ portfolioItem.title }}</p>
                  <p class="portfolio-item-description text-xs">{{ portfolioItem.description }}</p>
                  <small class="portfolio-item-tag" v-for="tag in portfolioItem.tags">
                    {{ tag }}
                  </small>
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
                <silent-box class="mb-3 w-40 h-40 border border-white"
                            :gallery="currentPortfolioItem.images"></silent-box>

                <a v-if="currentPortfolioItem.code" :href="currentPortfolioItem.code " target="_blank"
                   class="sm:float-right text-sm">code</a>
                <a v-if="currentPortfolioItem.link" :href="currentPortfolioItem.link" target="_blank"
                   class="mr-2 sm:float-right text-sm">view</a>

                <hr class="w-40 my-3 sm:hidden">

              </div>

              <div class="portfolio-item-body  sm:mt-0 sm:ml-5 text-xs sm:text-sm"
                   v-html="currentPortfolioItem.body"></div>
            </div>
          </div>
        </div>
      </div>

    </div>
  </div>
  <!--    Dev Portfolio Section End -->
</template>

<script>

import baffle from 'baffle';


export default {

  data() {
    return {


      currentPortfolioItem: null,

      portfolio: [
        {
          slug: "panzerprint",
          title: "Panzerprint 1",
          description: "Norweigan typist landing page",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#wordpress' ],

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio 2",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#vue', '#nuxt' ],

          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio 3",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#vue', '#nuxt' ],

          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio 4",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#vue', '#nuxt' ],

          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio 5",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#vue', '#nuxt' ],

          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio 6",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: [ '#vue', '#nuxt' ],

          live: null,

          body: "<h3>Welcome To My Portfolio</h3> <p>I have gone over various different styles and schemes of what my portfolio-old should look like</p> <p>Previously I've used templates, attempted to write the whole site in pure html,js,css</p> <p>Eventually my perfectionism lead me to this very site you are looking at which I have curated over time, everything you see, touch and feel, has all been written by me, with the help of frameworks and other widgets</p> <p>As design styles change and knowledge expands, so will my portfolio-old styles</p> <p><u>Role:</u>Design and Development</p>",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
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



.portfolio-section-wrapper, {
  scroll-behavior: smooth;
}

.portfolio-list-body {

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
    overflow-x: hidden;
  }

  .portfolio-item {

    padding-left: 17px;

    margin-bottom: 25px;

    transition: all .5s;

    display: flex;

    &:before {
      width: 1em;
      margin-left: -1em;
      content: "○";
      color: white;
    }

    &:hover {
      margin-left: 10px;


      .portfolio-item-tag {
        color: white;
        transition: all .5s;

      }

      &:before {
        content: "⦿";
      }
    }





  }
}

.portfolio-item-tag {
  font-size: .7em;
  color: #5A5A5A;
}

.portfolio-item-description {
  position: relative;
  &:after {

    content: "";
    height: 1px;
    background: white;
    position: absolute;
    width: 100%;
    bottom: 5px;
    margin-left: 5px;

  }

}



</style>
