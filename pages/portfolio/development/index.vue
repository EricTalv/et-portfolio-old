<template>
  <!--    Dev Portfolio Section Start -->

  <div class="about-section flex flex-wrap  justify-center">
    <div class="about-wrapper mt-44 w-3/5 c-min-width">
      <div class="about-nav-container w-full flex">


        <div class="about-nav-left flex items-end">

          <a class="mr-3 " style="font-size: 20px; height: 15px"
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

          <p class="text-sm">Portfolio</p>

          <div class="flex justify-end self-end">
            <p class="portfolio-development-link " v-if="!currentPortfolioViewItem" :class=" { 'text-gray-500': currentPortfolioViewItem }">development</p>

            <p  v-if="currentPortfolioViewItem" >{{ currentPortfolioViewItem.title }}</p>
            <a  v-else class="portfolio-design-link text-gray-500 " href="#">/design</a>

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
               class="portfolio-view-container min-w-full flex flex-wrap content-center ">
            <div v-if="currentPortfolioViewItem" class="min-w-full">

              <div class="portfolio-item-content block sm:flex">

                <div class="portfolio-view-item-sidebar-container w-40 mt-3 mb-5 mx-auto sm:mx-0">
                  <silent-box class="mb-3 w-40 h-40 border border-white"
                              :gallery="currentPortfolioViewItem.images"
                              :preview-count="1"></silent-box>

                  <p class="portfolio-sidebar-role">Research & Development</p>

                  <div class="portfolio-sidebar-links">
                    <a v-if="currentPortfolioViewItem.code" :href="currentPortfolioViewItem.code " target="_blank"
                       class=" text-sm">code</a>
                    <a v-if="currentPortfolioViewItem.link" :href="currentPortfolioViewItem.link" target="_blank"
                       class="mr-2 text-sm">live</a>
                  </div>


                  <ul class="portfolio-sidebar-tags">
                    <li v-for="tag in currentPortfolioViewItem.tags">{{ tag }}</li>
                  </ul>

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
          title: "Panzerprint",
          description: "Norweigan typist landing page",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#wordpress'],
          link: '#',

          body: "" +
            "<h2>Objective</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias blanditiis error expedita hic in quisquam saepe ullam velit veniam voluptate.</p> " +
            "<h2>Challenges</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad aspernatur ipsam perferendis quae similique voluptas?</p> " +
            "<h2>Outcome</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "",

          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },

        {
          slug: "this-portfolio",
          title: "This Portfolio",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#vue', '#nuxt'],

          live: null,

          body: "" +
            "<h2>Objective</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias blanditiis error expedita hic in quisquam saepe ullam velit veniam voluptate.</p> " +
            "<h2>Challenges</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad aspernatur ipsam perferendis quae similique voluptas?</p> " +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "",
          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },


        {
          slug: "this-portfolio",
          title: "This Portfolio",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#vue', '#nuxt'],

          live: null,

          body: "" +
            "<h2>Objective</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias blanditiis error expedita hic in quisquam saepe ullam velit veniam voluptate.</p> " +
            "<h2>Challenges</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad aspernatur ipsam perferendis quae similique voluptas?</p> " +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "",
          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },


        {
          slug: "this-portfolio",
          title: "This Portfolio",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#vue', '#nuxt'],

          live: null,

          body: "" +
            "<h2>Objective</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias blanditiis error expedita hic in quisquam saepe ullam velit veniam voluptate.</p> " +
            "<h2>Challenges</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad aspernatur ipsam perferendis quae similique voluptas?</p> " +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "",
          images: [
            {
              src: require('assets/images/image001.jpg'),
              description: 'The Power In My Hands',
            },
          ]
        },


        {
          slug: "this-portfolio",
          title: "This Portfolio",
          description: "How this portfolio was made",
          code: "https://github.com/EricTalv/et-portfolio",
          tags: ['#vue', '#nuxt'],

          live: null,

          body: "" +
            "<h2>Objective</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Alias blanditiis error expedita hic in quisquam saepe ullam velit veniam voluptate.</p> " +
            "<h2>Challenges</h2> " +
            "<p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ad aspernatur ipsam perferendis quae similique voluptas?</p> " +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "" +
            "<h2>Outcome</h2> " +
            "<p>Lorem  lorem 100 ipsum dolor sit amet, consectetur adipisicing elit. Beatae, porro.</p> " +
            "",
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

.portfolio-wrapper {
  &::-webkit-scrollbar {
    width: 20px;
    border: 1px solid white;
  }

  &::-webkit-scrollbar-thumb {
    border: 1px solid white;
    background-color: #5A5A5A;
  }

  scrollbar-color: #5A5A5A transparent;
}

.portfolio-item-content {
  justify-content: center;
}

.portfolio-item-body {
  margin-top: 5px;
  max-height: 260px;
  padding-right: 50px;

}

.portfolio-view-item-sidebar-container {
    .portfolio-sidebar-links {
      float: right;

      display: flex;
      flex-direction: column;

      margin-top: 5px;
      margin-bottom: 7px;

      a {
        margin: 2px 0 2px 0;

        &:hover {
          text-decoration: underline;
        }
      }
    }

    .portfolio-sidebar-role {
      font-size: .74em;
    }

    .portfolio-sidebar-tags {

      margin-top: 5px;

      li {
        font-size: .74em;
        color: #6b7280;
        transition: color .5s;

        &:hover {
          color: white;
        }
      }
    }
}

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
      width: 95%;
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

.portfolio-item-body  {
  text-align: justify;
  width: 45%;

  h2 {
    font-weight: bolder;
    text-decoration: underline;
  }

  p {
    margin-bottom: 15px;
  }

  @media only screen and (max-width: 768px) {
     width: 60%;
  }
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
