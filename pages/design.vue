<template>
  <main class="des-container">

    <div class="des-nav-tablet">
      <a class="des-nav-tablet__item" href="">about</a>
      <a class="des-nav-tablet__item" href="">dev</a>
    </div>

    <div class="des-title">
      DESIGN
    </div>


    <div class="des-list">

      <simplebar
        :style="`--scrollPos: ${scrollPosition}; --scrollPosDeg: ${scrollPositionDeg};`"
        class="des-list__simplebar"

        data-simplebar-auto-hide="false"
        data-simplebar-direction="rtl"
        @scroll="getScrollPosition">
        <button class="des-item" @click="showModal(projectList.project_one)">
          <img src="../assets/images/design/excalibur.png" alt="">
        </button>
        <button class="des-item" @click="showModal(projectList.project_one)">
          <img src="../assets/images/design/messed-up.png" alt="">
        </button>
        <button class="des-item" @click="showModal(projectList.project_one)">
          <img src="../assets/images/design/red-mist.png" alt="">
        </button>
        <button class="des-item" @click="showModal(projectList.project_one)">
          <img src="../assets/images/design/silent.png" alt="">
        </button>
        <button class="des-item" @click="showModal(projectList.project_one)">
          <img src="../assets/images/design/sinful.png" alt="">
        </button>
      </simplebar>


    </div>
    <div class="des-nav">
      <a class="des-nav__item" href="">about</a>
      <a class="des-nav__item" href="">dev</a>

    </div>


    <div v-if="isModalVisible" class="des-modal">
      <button class="des-modal__close" @click="closeModal()">X</button>

      <h1 class="des-modal__title">{{ this.currentModalProject.title }}</h1>

      <div class="des-modal__body-image-wrapper">
        <div class="des-modal__body">
          <p v-for="paragraph in this.currentModalProject.description">{{ paragraph }}</p>
        </div>

        <silent-box :gallery="this.currentModalProject.images" :preview-count="1"></silent-box>

      </div>

      <a href="#">
        <img alt="" class="des-modal__github" src="../assets/images/github.svg">
      </a>

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

      projectList: {
        project_one: {
          title: "This Portfolio ONE",
          description: [
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab odio provident quo voluptate. Doloribus et fugit officiis quaerat reprehenderit sunt?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Debitis eaque enim est excepturi facilis illum repellat veniam? Alias blanditiis cum dolore, quae qui quibusdam sequi. Architecto debitis dolor ipsa molestiae nobis repellat repudiandae, sequi ut!\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ducimus magnam odit placeat quae reiciendis vero.\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, eum exercitationem impedit laudantium officiis voluptatum?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquam aut eligendi id impedit labore magni officiis omnis quae repellendus vel! Atque aut consequatur ea eaque facilis fugit illo in reiciendis?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab, architecto blanditiis corporis dicta, ducimus eaque explicabo fugit harum hic ipsam minus ratione. A, aliquid autem beatae ea facilis fugit illum placeat quod sequi totam! Architecto autem expedita in ipsam labore omnis ratione rem rerum veritatis voluptatum! Accusamus, aliquid beatae commodi excepturi, iste laboriosam libero mollitia odit porro quia quos repellendus, voluptate? Corporis, praesentium, voluptate? Accusantium consequatur deleniti deserunt distinctio error et eum eveniet ex fuga iusto, modi molestiae, pariatur placeat quia quo sequi vitae voluptas voluptatibus. Aliquid cum hic ipsum possimus recusandae. Ab, laborum, ut. Aut minima quia quidem velit.\n"
          ],
          images: [
            {
              src: require('assets/images/design/excalibur.png'),
              srcSet: require('assets/images/design/excalibur.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
          ]

        },
        project_two: {
          title: "This Portfolio TWO",
          description: [
            "This is some text one",
            "This is some text Three",
            "This is some text Two"
          ]
        },
        project_three: {
          title: "This Portfolio THREE",
          description: [
            "This is some text one",
            "This is some text Three",
            "This is some text Two"
          ]

        }
      }
    }
  },

  methods: {
    closeModal() {
      this.isModalVisible = false
    },

    showModal(currentModalProject) {
      this.isModalVisible = true
      this.currentModalProject = currentModalProject
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
.des-container, .des-item, .des-nav-tablet {
  color: white;
  font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
  text-shadow: 0px 0px 10px #000000;
}

.des-title {
  font-size: 3em;
  padding: 20px 0 20px 0;
  width: 100%;
  text-align: center;
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
}

.des-nav__item {
  font-size: 2em;
}

// =  Dev Modal - mobile
.des-modal {

  padding: 20px;

  position: absolute;
  width: 100%;
  height: 100%;

  top: 0;

  background-color: black;

  color: white;

  .des-modal__close {
    background-color: white;
    color: black;
    width: 27px;
    float: right;
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
    height: 99%;


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

.des-nav-tablet {
  display: none;
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

  .des-title {
    text-align: left;
    padding-left: 9vw;
    pointer-events: none;


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


  // =  Dev Modal - tablet
  .des-modal {


    .des-modal__close {

    }

    .des-modal__title {

    }

    .des-modal__github {

    }

    .des-modal__body-image-wrapper {
      .des-modal__body {
        width: 60vw;

        font-size: .9em;

      }
    }

  }


}


// ====  Dev media queries - ON DESKTOP ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-tablet) {

  // = Deb Simplebar - desktop
  .des-list__simplebar {
    height: 90vh;
    direction: rtl;
  }

  // =  Dev Background - desktop
  .des-container {
    background-image: url("../assets/images/big-bg3.png");
    background-size: 100% 1100px;
  }

  // =  Dev Text Defaults - desktop
  .des-container, .des-item {

  }

  .des-title {
    padding-left: 0;
    margin-top: -100px;

    display: flex;

    justify-content: center;
    align-items: center;

    height: 100%;
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

      .des-modal__body {
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

    top: calc(var(--scrollPos) - (var(--scrollPos) * .7)) !important;


  }

}

/* ================ ================ ================  SILENTBOX STYLES ================ ================ ================ */

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

  width: 100%;

}

.silentbox-item > img {
  height: 200px;

  object-fit: cover;
}

@media (min-width: 930px) {
  #silentbox-gallery {
    flex-flow: column;
    justify-content: space-between;
    margin: 0;
    padding: 0 5vw 0 5vw;
  }

  .silentbox-item {
    margin-right: 0;
  }

  .silentbox-item > img {
    max-width: 90% ;
    height: 100%;
  }


}


</style>
