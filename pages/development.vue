<template>
  <main class="dev-container">

    <div class="dev-nav-tablet">
      <a class="dev-nav-tablet__item" href="/about">about</a>
      <a class="dev-nav-tablet__item" href="/design">design</a>
    </div>

    <div class="des-title-container">
      <button class="des-title-container__title-btn" @click="showAboutModal()">
        DEVELOPMENT
      </button>
    </div>


    <div class="dev-list">

      <simplebar
        :style="`--scrollPos: ${scrollPosition}; --scrollPosDeg: ${scrollPositionDeg};`"
        class="dev-list__simplebar"

        data-simplebar-auto-hide="false"
        data-simplebar-direction="rtl"
        @scroll="getScrollPosition">
        <button class="dev-item" @click="showModal(projectList.project_one)">This Portfolio</button>
        <button class="dev-item" @click="showModal(projectList.project_one)">This Portfolio</button>
        <button class="dev-item" @click="showModal(projectList.project_one)">This Portfolio</button>
        <button class="dev-item" @click="showModal(projectList.project_one)">This Portfolio</button>
        <button class="dev-item" @click="showModal(projectList.project_one)">This Portfolio</button>
      </simplebar>


    </div>
    <div class="dev-nav">
      <a class="dev-nav__item" href="">about</a>
      <a class="dev-nav__item" href="">design</a>

    </div>


    <div v-if="isModalVisible" class="dev-modal">
      <button class="dev-modal__close" @click="closeModal()">X</button>

      <h1 class="dev-modal__title">{{ this.currentModalProject.title }}</h1>

      <div class="dev-modal__body-image-wrapper">
        <div class="dev-modal__body">
          <p v-for="paragraph in this.currentModalProject.description">{{ paragraph }}</p>
        </div>

        <silent-box :gallery="this.currentModalProject.images" :preview-count="3"></silent-box>

      </div>

      <a href="#">
        <img alt="" class="dev-modal__github" src="../assets/images/github.svg">
      </a>

    </div>

    <div v-if="aboutModal.visible" class="des-about-modal">
      <button class="des-about-modal__close" @click="closeModal()"></button>

      <div class="des-about-modal-body-wrapper">
        <div class="des-about-modal__title">{{ this.aboutModal.title }}</div>
        <div class="des-about-modal__body">{{ this.aboutModal.desc }}</div>
      </div>
    </div>


  </main>
</template>

<script>

import simplebar from 'simplebar-vue';
import 'simplebar/dist/simplebar.min.css';

export default {
  name: "development",
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
        title: 'On The Look For a Semicolon',
        desc: 'Here are some of my works in the web-development realm'
      },

      projectList: {
        project_one: {
          title: "This Portfolio",
          description: [
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab, architecto blanditiis corporis dicta, ducimus eaque explicabo fugit harum hic ipsam minus ratione. A, aliquid autem beatae ea facilis fugit illum placeat quod sequi totam! Architecto autem expedita in ipsam labore omnis ratione rem rerum veritatis voluptatum! Accusamus, aliquid beatae commodi excepturi, iste laboriosam libero mollitia odit porro quia quos repellendus, voluptate? Corporis, praesentium, voluptate? Accusantium consequatur deleniti deserunt distinctio error et eum eveniet ex fuga iusto, modi molestiae, pariatur placeat quia quo sequi vitae voluptas voluptatibus. Aliquid cum hic ipsum possimus recusandae. Ab, laborum, ut. Aut minima quia quidem velit.\n"
          ],
          images: [
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: 'Sunken dreams II. by Arbebuk',
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
.dev-container {
  width: 100%;

  background-color: black;
  background-image: url("../assets/images/mobile-bg.png");
  background-repeat: no-repeat;
  background-position: center;

  background-size: 100% 1500px;

  display: flex;
  flex-flow: column;
}

// =  Dev Text Defaults - mobile
.dev-container, .dev-item, .dev-nav-tablet, .des-title-container__title-btn {
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

.dev-title {
  font-size: 3em;
  padding: 20px 0 20px 0;
  width: 100%;
  text-align: center;
}

// =  Dev List - mobile
.dev-list {
  width: 100%;
  height: 70vh;

  overflow-y: auto;
}

// =  Dev List Item - mobile
.dev-item {
  background-image: url("../assets/images/dev-item-mobile-bg.png");
  background-repeat: no-repeat;
  background-size: cover;

  color: white;
  width: 100%;

  padding: 50px;

  text-align: center;

  font-size: 1.5em;

  margin-bottom: 20px;

  &:last-child {
    margin-bottom: 0;
  }
}

// =  Dev Nav - mobile
.dev-nav {
  display: flex;
  justify-content: space-around;
  padding-top: 6%;
}

.dev-nav__item {
  font-size: 2em;
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
.dev-modal {

  padding: 20px;

  position: absolute;
  width: 100%;
  height: 100%;

  top: 0;

  background-color: black;

  color: white;

  .dev-modal__close {
    background-color: white;
    color: black;
    width: 27px;
    float: right;
  }

  .dev-modal__title {
    font-family: 'IBM Plex Mono', monospace;
    font-style: italic;
    text-decoration: underline;
  }

  .dev-modal__github {
    position: absolute;
    width: 23px;
    top: 72px;
    right: 22px;
  }


  .dev-modal__body-image-wrapper {
    height: 99%;


    .dev-modal__body {

      &::-webkit-scrollbar {
        background: transparent;
        width: 5px;
      }


      &::-webkit-scrollbar-thumb {
        background: white;
        border-radius: 50px;

      }

      padding-top: 10px;
      padding-left: 5px;
      padding-right: 15px;

      padding: 10px 25px 0 5px;

      width: 70vw;
      max-height: 65%;


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

.dev-nav-tablet {
  display: none;

  .dev-nav-tablet__item {
    transition: all .5s;

    &:hover {
      letter-spacing: 5px;

    }
  }
}

/* BreakPoints */
$breakpoint-tablet: 930px;
$breakpoint-mobile: 501px;

// ====  Dev media queries - ON TABLET ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-mobile) {

  // = Deb Simplebar - tablet
  .dev-list__simplebar {
    height: 70vh;
    direction: rtl;
  }

  // =  Dev Background - tablet
  .dev-container {

  }

  // =  Dev Text Defaults - tablet
  .dev-container, .dev-item {

  }

  .des-title-container {
    text-align: left;
    padding-left: 9vw;
  }

  // =  Dev List - tablet
  .dev-list {
    height: auto;
    overflow: unset;

    position: fixed;
    bottom: 0;

  }

  // =  Dev List Item - tablet
  .dev-item {
    padding: 70px;
    width: 75%;


    &:last-child {

    }
  }

  // =  Dev Nav - tablet
  .dev-nav {
    display: none;
  }

  .dev-nav-tablet {
    display: flex;
    justify-content: space-between;

    padding: 5vh 9vw 6vh 9vw;

    .dev-nav-tablet__item {
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
  .dev-modal {


    .dev-modal__close {

    }

    .dev-modal__title {

    }

    .dev-modal__github {

    }

    .dev-modal__body-image-wrapper {
      .dev-modal__body {
        width: 60vw;

        font-size: .9em;

      }
    }

  }


}


// ====  Dev media queries - ON DESKTOP ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-tablet) {

  // = Deb Simplebar - desktop
  .dev-list__simplebar {
    height: 90vh;
    direction: rtl;
  }

  // =  Dev Background - desktop
  .dev-container {
    background-image: url("../assets/images/big-bg3.png");
    background-size: 100% 1100px;
  }

  // =  Dev Text Defaults - desktop
  .dev-container, .dev-item {

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
  .dev-list {
    width: 50%;
    position: fixed;
    right: 0;
    bottom: 0;

  }

  // =  Dev List Item - desktop
  .dev-item {
    width: 40vw;

    &:last-child {

    }
  }

  // =  Dev Nav - desktop
  .dev-nav-tablet {

    width: 50%;
    display: flex;
    justify-content: space-between;
    padding: 40px 40px 0 40px;

    .dev-nav-tablet__item {

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
  .dev-modal {


    .dev-modal__close {

    }

    .dev-modal__title {

    }

    .dev-modal__github {

    }

    .dev-modal__body-image-wrapper {
      display: flex;

      .dev-modal__body {
        width: 90vw;
        max-height: 100%;
        max-width: 600px;
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

  top: calc(var(--scrollPos) - (var(--scrollPos) * .21)) !important;

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

    padding: 10px 3vw 0 3vw;

  }

  .simplebar-track {
    background-image: url("../assets/images/scroll-bg-btm-white.png");
  }

  .simplebar-scrollbar:before {

    top: calc(var(--scrollPos) - (var(--scrollPos) * .12)) !important;


  }

}

/* ================ ================ ================  SILENTBOX STYLES ================ ================ ================ */


/* DEV - SILENTBOX MOBILE VIEW */
#silentbox-gallery {
  display: flex;
  justify-content: space-around;
  max-width: 100%;
  overflow: hidden;
  padding: 10px;
  margin-top: 15px;
}

.silentbox-item {
  margin-right: 20px;

}

.silentbox-item > img {
  height: 211px;
  max-width: 145px;
  object-fit: cover;
}


/* DEv - SILENTBOX MOBILE VIEW */

@media (min-width: 930px) {
  #silentbox-gallery {
    flex-flow: column;
    justify-content: space-between;
    margin: 0;
    padding: 0;
  }

  .silentbox-item {
    margin-right: 0;

  }

  .silentbox-item > img {
    max-width: 90% !important;
  }


}


</style>
