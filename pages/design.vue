<template>
  <main class="des-container">

    <div class="des-nav-tablet">
      <a class="des-nav-tablet__item" href="/about">about</a>
      <a class="des-nav-tablet__item" href="/development">dev</a>
    </div>

    <div class="des-title-container">
      <button class="des-title-container__title-btn" @click="showAboutModal()">
        DESIGN
      </button>
    </div>


    <div class="des-list">

      <simplebar
        :style="`--scrollPos: ${scrollPosition}; --scrollPosDeg: ${scrollPositionDeg};`"
        class="des-list__simplebar"

        data-simplebar-auto-hide="false"
        data-simplebar-direction="rtl"
        @scroll="getScrollPosition">

        <button class="des-item" @click="showModal(projectList.etxp)">
          <img alt="" src="../assets/images/design/etxp-posters/coverpic.jpg">
        </button>
        <button class="des-item" @click="showModal(projectList.this_portfolio)">
          <img alt="" src="../assets/images/design/this-portfolio.jpg">
        </button>


      </simplebar>


    </div>
    <div class="des-nav">
      <a class="des-nav__item" href="">about</a>
      <a class="des-nav__item" href="">dev</a>

    </div>


    <div v-if="isModalVisible" class="des-modal">
      <button class="des-modal__close" @click="closeModal()"></button>


      <div class="des-modal__body-image-wrapper">


        <div class="des-modal-body-wrapper">

          <h1 class="des-modal__title">{{ this.currentModalProject.title }}</h1>

          <div class="des-modal__body">
            <p v-for="paragraph in this.currentModalProject.description" v-html="paragraph"></p>

          </div>

        </div>

        <silent-box :gallery="this.currentModalProject.images" :preview-count="1"></silent-box>

      </div>

    </div>


    <div v-if="aboutModal.visible" class="des-about-modal">
      <button class="des-about-modal__close" @click="closeModal()"></button>

      <div class="des-about-modal-body-wrapper">
        <div class="des-about-modal__title">{{ this.aboutModal.title }}</div>
        <div class="des-about-modal__body" v-html="this.aboutModal.desc"></div>
      </div>
    </div>


  </main>
</template>

<script>

import simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';

export default {
  name: "design",
  components: {
    simplebar
  },

  data() {
    return {
      isModalVisible: false,
      currentModalProject: null,

      scrollPosition: 0 + "%",
      scrollPositionDeg: 0 + "%",

      aboutModal: {
        visible: false,
        title: 'In The Name Of Design',
        desc: `Here's a deeper look into my thought process when it comes to various kinds of design work`
      },

      projectList: {
        etxp: {
          title: "ETXP",
          description: [
            "ETXP - is my personal digital media experimentation playground, where I try out different techinques and styles",
            `<a target="_blank" href="https://www.instagram.com/et_experience/"><u>See more of ETXP here</u></a>`,

          ],
          images: [
            {
              src: require('assets/images/design/etxp-posters/coverpic.jpg'),
              srcSet: require('assets/images/design/etxp-posters/coverpic.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/xanax.jpg'),
              srcSet: require('assets/images/design/etxp-posters/xanax.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/excalibur.jpg'),
              srcSet: require('assets/images/design/etxp-posters/excalibur.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/lost-in-space.jpeg'),
              srcSet: require('assets/images/design/etxp-posters/lost-in-space.jpeg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/messed-up.jpg'),
              srcSet: require('assets/images/design/etxp-posters/messed-up.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/nothing-really-matters.jpg'),
              srcSet: require('assets/images/design/etxp-posters/nothing-really-matters.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/placebo.jpg'),
              srcSet: require('assets/images/design/etxp-posters/placebo.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/red-mist.jpg'),
              srcSet: require('assets/images/design/etxp-posters/red-mist.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/silent.jpg'),
              srcSet: require('assets/images/design/etxp-posters/silent.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/sinful.jpg'),
              srcSet: require('assets/images/design/etxp-posters/sinful.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/theperfect-circle.jpg'),
              srcSet: require('assets/images/design/etxp-posters/theperfect-circle.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },

            {
              src: require('assets/images/design/etxp-posters/everythings-the-same.jpg'),
              srcSet: require('assets/images/design/etxp-posters/everythings-the-same.jpg'),
              description: '',
              thumbnailWidth: '1600px',
            },
          ]
        },

        this_portfolio: {
          title: "This Portfolio",
          description: [
            "Much of my work can be derived by the brutalism movement.",
            "I enjoy the principles of being bold, brave and brutalic, thus was this design born.",
            "But besides my enjoyment to experimentalism and exploration, there are certain rules when it comes to web-design.",
            "Granted, here today, I am definitely going to offend many accessibility users and UX designers, I have attempted to stay true to one principle and that is simplicity.",
            "Though the design might not be that intuitive, like the rotating scrollbar, or the disguised titles as buttons, I have kept away from endless monotony of pages, sub-menus and whatnot.",
            "The message I wish to convey is that I'm neither truly a dev or a designer, but something of an visual explorer, utilizing web technologies, blending graphic design and interactivity, bending the rules of design as I see fit.",
            "I believe personal portfolios should convey some insight to the designers/developers character, because character shows who we truly are.",


          ],
          images: [
            {
              src: require('assets/images/mobile-bg.png'),
              srcSet: require('assets/images/mobile-bg.png'),
              description: '',
              thumbnailWidth: '1600px',
            },
          ]
        },

        datagambit: {
          title: "DataGambit",
          description: [
            "DataGambit"

          ],
          images: [
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: '',
              thumbnailWidth: '1600px',
            },
          ]
        },

        greensaar: {
          title: "GreenSaar",
          description: [
            "Greensaar",

          ],
          images: [
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: '',
              thumbnailWidth: '1600px',
            },
          ]
        },
      }
    }
  },

  methods: {
    closeModal() {
      this.isModalVisible = false
      this.aboutModal.visible = false
    },

    showModal(currentModalProject) {
      this.isModalVisible = true
      this.currentModalProject = currentModalProject
    },

    showAboutModal() {
      this.aboutModal.visible = true
    },

    /* Get scrollbar-thumb position */
    getScrollPosition: function (el) {
      let elementHeight = el.target.offsetHeight;
      let scrollTopPos = el.target.scrollTop;
      let maxScrollHeight = el.target.scrollHeight;

      /* This is to calculate the scrollbar-thumb position in percentage */
      let scrollPositionPercentage = Math.ceil(
        (scrollTopPos / (maxScrollHeight - elementHeight)) * 100
      );

      this.scrollPosition = scrollPositionPercentage + "%";
      this.scrollPositionDeg = scrollPositionPercentage * 1.8 + "deg";

      console.log(this.scrollPositionDeg);
    },
  },

  computed: {}

}
</script>


<style lang="scss" scoped>


// ====  ON MOBILE
// =  Dev Background - mobile
.des-container {
  width: 100%;

  background-color: black;
  background-image: url("../assets/images/mobile-bg.png");
  background-repeat: repeat-y;
  background-position: center;

  background-size: 100% 1500px;

  display: flex;
  flex-flow: column;
}

// =  Dev Text Defaults - mobile
.des-container, .des-item, .des-nav-tablet, .des-title-container__title-btn {
  color: white;
  font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
  text-shadow: 0px 0px 10px #000000;
}

.des-title-container {
  font-size: 3em;
  padding: 20px 0 20px 0;
  width: 100%;
  text-align: center;

  .des-title-container__title-btn {
    outline: none;

    transition: all .5s;

    &:hover {
      letter-spacing: 5px;
    }

  }

}

// =  Dev List - mobile
.des-list {
  width: 100%;
  height: 70vh;

  overflow-y: auto;
}

// =  Dev List Item - mobile
.des-item {
  background-repeat: no-repeat;
  background-size: cover;

  color: white;
  width: 100%;

  text-align: center;
  font-size: 1.5em;

  padding: 50px;

  margin-bottom: 20px;



  &:last-child {
    margin-bottom: 0;
  }
}

// =  Dev Nav - mobile
.des-nav {
  display: flex;
  justify-content: space-around;
  padding-top: 6%;


  .des-nav__item {
    font-size: 2em;



  }

}

// =  Dev ABOUT Modal - mobile
.des-about-modal {
  position: absolute;
  width: 100%;
  height: 100%;

  background-color: black;
  color: white;

  padding: 50px;

  font-family: 'IBM Plex Mono', monospace;


  .des-about-modal__close {
    background-image: url("./assets/images/closebutton.svg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;

    float: right;

    width: 30px;
    height: 30px;
  }


  .des-about-modal-body-wrapper {
    height: 100%;

    display: flex;
    justify-content: center;
    align-items: center;
    flex-flow: column;


    .des-about-modal__title {
      text-decoration: underline;
      margin-bottom: 10px;
    }

    .des-about-modal__body {
      font-size: .8em;

      text-align: center;

      padding: 0 100px;

    }

  }
}


// =  Dev Modal - mobile
.des-modal {

  padding: 0;

  position: absolute;
  width: 100%;
  height: 100%;

  top: 0;

  background-color: black;

  color: white;

  .des-modal__close {
    background-image: url("./assets/images/closebutton.svg");
    background-repeat: no-repeat;
    background-position: center;
    background-size: cover;

    position: absolute;

    right: 0;
    width: 30px;
    height: 30px;
  }

  .des-modal__title {
    font-family: 'IBM Plex Mono', monospace;
    font-style: italic;
    text-decoration: underline;
  }

  .des-modal__github {
    position: absolute;
    width: 23px;
    top: 72px;
    right: 22px;
  }


  .des-modal__body-image-wrapper {
    height: 100%;



    .des-modal-body-wrapper {

      padding: 20px;

      .des-modal__body {



        &::-webkit-scrollbar {
          background: transparent;
          width: 5px;
        }


        &::-webkit-scrollbar-thumb {
          background: white;
          border-radius: 50px;

        }


        padding: 10px 25px 0 5px;

        width: 70%;
        max-height: 500px;


        font-family: "IBM Plex Mono", monospace;
        font-weight: 300;
        font-size: .8em;

        overflow: auto;


        p {
          margin-bottom: 15px;

        }
      }
    }
  }

}

.des-nav-tablet {
  display: none;

  .des-nav-tablet__item {
    transition: all .5s;

    &:hover {
      letter-spacing: 5px;

    }

  }

}

/* BreakPoints */
$breakpoint-desktopxl: 930px;
$breakpoint-tablet: 930px;
$breakpoint-mobile: 501px;

// ====  Dev media queries - ON TABLET ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-mobile) {

  // = Deb Simplebar - tablet
  .des-list__simplebar {
    height: 70vh;
    direction: rtl;
  }

  // =  Dev Background - tablet
  .des-container {

  }

  // =  Dev Text Defaults - tablet
  .des-container, .des-item {

  }

  .des-title-container {
    text-align: left;
    padding-left: 9vw;


  }

  // =  Dev List - tablet
  .des-list {
    height: auto;
    overflow: unset;

    position: fixed;
    bottom: 0;

  }

  // =  Dev List Item - tablet
  .des-item {
    width: 85%;

    padding: 0 120px;

    margin-bottom: 100px;

    &:last-child {
    }
  }

  // =  Dev Nav - tablet
  .des-nav {
    display: none;
  }

  .des-nav-tablet {
    display: flex;
    justify-content: space-between;

    padding: 5vh 9vw 6vh 9vw;

    .des-nav-tablet__item {
      font-size: 1.5em;
    }

  }

  // =  Dev ABOUT Modal - tablet
  .des-about-modal {

    .des-about-modal__close {

    }


    .des-about-modal-body-wrapper {

      .des-about-modal__title {
        font-size: 2em;
        margin-bottom: 20px;
      }

      .des-about-modal__body {
        font-size: 1.5em;
      }

    }

  }


  // =  Dev Modal - tablet
  .des-modal {


    .des-modal__close {

    }

    .des-modal__title {

    }

    .des-modal__github {

    }

    .des-modal__body-image-wrapper {


      .des-modal-body-wrapper {


        .des-modal__body {
          width: 60vw;

          max-height: 300px;


          font-size: .9em;

        }
      }
    }

  }


}


// ====  Dev media queries - ON DESKTOP ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-tablet) {

  // = Dev Simplebar - desktop
  .des-list__simplebar {
    height: 90vh;
    direction: rtl;
  }

  // =  Dev Background - desktop
  .des-container {
    background-image: url("../assets/images/desk-bg.webp");
    background-size: 100% 1100px;
  }

  // =  Dev Text Defaults - desktop
  .des-container, .des-item {

  }

  .des-title-container {
    padding-left: 0;

    display: flex;

    justify-content: center;
    align-items: center;

    height: 80%;
    width: 50%;
  }

  // =  Dev List - desktop
  .des-list {
    width: 50%;
    position: fixed;
    right: 0;
    bottom: 0;

  }

  // =  Dev List Item - desktop
  .des-item {
    width: 42vw;

    padding: 0 30px;

    img {
      width: 100%;

    }

    &:last-child {

    }
  }

  // =  Dev Nav - desktop
  .des-nav-tablet {

    width: 50%;
    display: flex;
    justify-content: space-between;
    padding: 40px 40px 0 40px;

    .des-nav-tablet__item {

    }

  }

  // =  Dev ABOUT Modal - desk
  .des-about-modal {

    position: fixed;

    height: 40%;
    width: 70%;

    top: 30%;
    transform: translateY(-50%);
    left: 50%;
    transform: translateX(-50%);


    .des-about-modal__close {

    }


    .des-about-modal-body-wrapper {


      .des-about-modal__title {
        font-size: 1em;
        margin-bottom: 20px;
      }

      .des-about-modal__body {
        font-size: .9em;
      }

    }

  }

  // =  Dev Modal - desktop
  .des-modal {


    .des-modal__close {

    }

    .des-modal__title {
    }

    .des-modal__github {

    }

    .des-modal__body-image-wrapper {
      display: flex;

      align-items: center;

      .des-modal-body-wrapper {

        margin-top: -100px;

        padding: 50px;

        width: 50%;

        .des-modal__body {
          width: 100%;
          max-height: 90%;
        }
      }


    }

  }

}


</style>


<style>

/* ================ ================ ================  SIMPLEBAR STYLES ================ ================ ================ */


.simplebar-scrollbar > * {
  box-sizing: border-box;
}

.simplebar-scrollbar {
  box-sizing: border-box;

  position: relative;
  width: 60px;
  right: -30px;

  mix-blend-mode: exclusion;
}

.simplebar-scrollbar:before {

  top: calc(var(--scrollPos) - (var(--scrollPos) * .8)) !important;

  background-image: url("./assets/images/scroll-thumb-arrow2.svg") !important;
  background-repeat: no-repeat;
  background-position-x: center;

  mix-blend-mode: exclusion;

  transform: rotate(calc(var(--scrollPosDeg) * -1)) !important;
  transform-origin: 50% 50%;

  position: absolute !important;
  width: 100% !important;
  height: 75px !important;


  left: 0;
  right: 0;

  z-index: -1 !important;

  border-radius: 0;
  opacity: 1 !important;

}


.simplebar-track {
  padding: 0px 30px 0 30px;
  margin: 0 30vw 0 9vw;
  background-image: url("../assets/images/scroll-bg.png");
  background-size: contain;
}

/* ================ ================ ================  SIMPLEBAR STYLES MEDIA QUERIES ================ ================ ================ */

/* ====  Dev media queries - ON DESKTOP ==== ==== ==== ==== ==== ==== ==== ==== ==== ==== */
@media (min-width: 930px) {
  .simplebar-track {
    margin-left: 2vw;

    padding: 10px 2.5vw 0 2.5vw;

    background-size: cover;

  }

  .simplebar-track {
    background-image: url("../assets/images/scroll-bg-btm-white.png");
  }

  .simplebar-scrollbar:before {

    top: calc(var(--scrollPos) - (var(--scrollPos) * .19)) !important;


  }

}

/* ================ ================ ================  SILENTBOX STYLES ================ ================ ================ */

#silentbox-gallery {
  display: flex;
  justify-content: space-around;
  max-width: 100%;
  overflow: hidden;
  margin-top: 15px;
  height: 100%;
}

.silentbox-item {

  width: 100%;

}

.silentbox-item > img {

  object-fit: cover;
}


/* DES - SILENTBOX - DESK */
@media (min-width: 930px) {
  #silentbox-gallery {
    margin: 0;
    padding: 0;
    width: 50%;
  }

  .silentbox-item {
    margin-right: 0;
  }

  .silentbox-item > img {
    width: 100%;
    height: 100%;
  }


}


</style>
