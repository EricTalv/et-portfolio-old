<template>
  <!--    Dev Portfolio Section Start -->

  <div class="about-section flex flex-wrap  justify-center">
    <div class="about-wrapper mt-44 w-3/5 c-min-width">
      <div class="about-nav-container w-full flex">


        <div class="about-nav-left flex items-end">

          <a class="mr-3 self-center" style="font-size: 20px"
             v-if="currentPortfolioViewItem"
             @click="removeCurrentPortfolioViewItem"
             href="#portfolio-list">
            <svg class="back-arrow" width="19" height="8" viewBox="0 0 19 8" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path
                d="M0.646447 3.64644C0.451184 3.84171 0.451184 4.15829 0.646447 4.35355L3.82843 7.53553C4.02369 7.73079 4.34027 7.73079 4.53553 7.53553C4.7308 7.34027 4.7308 7.02369 4.53553 6.82842L1.70711 4L4.53553 1.17157C4.7308 0.976309 4.7308 0.659726 4.53553 0.464464C4.34027 0.269202 4.02369 0.269202 3.82843 0.464464L0.646447 3.64644ZM19 3.5L1 3.5L1 4.5L19 4.5L19 3.5Z"
                />
            </svg>
          </a>

          <a href="#">about</a>
          <a class="mx-3" href="#">contact</a>

        </div>

        <div class="about-nav-right w-full text-right flex flex-col">

          <p class="text-sm" v-bind:class="{ hidden: currentPortfolioViewItem }">Portfolio</p>

          <div class="flex justify-end self-end">
            <p class="portfolio-development-link" :class=" { 'text-gray-500': currentPortfolioViewItem }">development</p>

            <p v-if="currentPortfolioViewItem" >/{{ currentPortfolioViewItem.title }}</p>
            <a v-else class="portfolio-design-link text-gray-500 " href="#">/design</a>

          </div>
        </div>


      </div>

      <hr class="my-2 ">

      <div id="dev-portfolio-container" class="portfolio-container ">
        <div class="portfolio-wrapper h-full w-full flex flex-row flex-nowrap overflow-x-hidden">

          <!--   Portfolio List Start     -->
          <div class="portfolio-list-wrapper min-w-full">
            <div class="portfolio-list-body ">
              <ul id="portfolio-list" class="portfolio-unordered-list">
                <li class="portfolio-item" v-for="portfolioItem of portfolio" :key="portfolioItem.slug">
                  <a @click="setCurrentPortfolioViewItem(portfolioItem)" :href="`#${portfolioItem.slug}`">
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
          <!--   Portfolio List End     -->


          <!--   Portfolio Item View Start     -->
          <div v-if="currentPortfolioViewItem" :id="currentPortfolioViewItem.slug"
               class="portfolio-sec-wrapper min-w-full flex flex-wrap content-center ">
            <div v-if="currentPortfolioViewItem" class="min-w-full">

              <div class="portfolio-content w-full block sm:flex py-2 px-10">
                <div class="w-48 mx-auto sm:mx-0">
                  <silent-box class="mb-3 w-40 h-40 border border-white"
                              :gallery="currentPortfolioViewItem.images"
                              :preview-count="1"></silent-box>

                  <a v-if="currentPortfolioViewItem.code" :href="currentPortfolioViewItem.code " target="_blank"
                     class="sm:float-right text-sm">code</a>
                  <a v-if="currentPortfolioViewItem.link" :href="currentPortfolioViewItem.link" target="_blank"
                     class="mr-2 sm:float-right text-sm">view</a>

                  <hr class="w-40 my-3 sm:hidden">

                </div>

                <div class="portfolio-item-body  sm:mt-0 sm:ml-5 text-xs sm:text-sm"
                     v-html="currentPortfolioViewItem.body"></div>
              </div>
            </div>
          </div>
        </div>

      </div>
      <!--   Portfolio Item View End    -->


    </div>
  </div>
  <!--    Dev Portfolio Section End -->
</template>

<script>

import baffle from 'baffle';


export default {

  data() {
    return {


      currentPortfolioViewItem: null,

      portfolio: [
        {
          slug: "panzerprint",
          title: "Panzerprint 1",
          description: "Norweigan typist landing page",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#wordpress'],

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
          tags: ['#vue', '#nuxt'],

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
          tags: ['#vue', '#nuxt'],

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
          tags: ['#vue', '#nuxt'],

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
          tags: ['#vue', '#nuxt'],

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
          tags: ['#vue', '#nuxt'],

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

    setCurrentPortfolioViewItem(portfolioItem) {
      this.currentPortfolioViewItem = portfolioItem;
    },

    removeCurrentPortfolioViewItem() {
      this.currentPortfolioViewItem = null;

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

.portfolio-design-link {

  transition: all .5s;
  &:hover {
    color: white;
    text-decoration: underline;

  }
}

.back-arrow {
  fill: #6b7280;

  &:hover {
    fill: white;
  }
}
.about-nav-left > a {
  color: #6b7280;
  transition: color .5s;

  &:hover {
    color: white;
  }
}

.portfolio-list-wrapper {
  display: flex;
  justify-content: center;
}

.portfolio-wrapper, {
  scroll-behavior: smooth;
}

.portfolio-list-body {

  max-height: 260px;
  overflow-y: auto;
  width: 90%;
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

    margin-bottom: 25px;

    transition: all .5s;

    display: flex;

    a {
      width: 90%;
    }

    &:before {
      width: 1em;
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

  overflow: hidden;

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
