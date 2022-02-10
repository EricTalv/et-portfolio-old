<template>
  <main class="dev-container">

    <div class="dev-nav-tablet">
      <a href="" class="dev-nav-tablet__item">about</a>
      <a href="" class="dev-nav-tablet__item">design</a>
    </div>

    <div class="dev-title">
      DEVELOPMENT
    </div>


    <div class="dev-list">

      <simplebar
        @scroll="getScrollPosition"
        :style="`--scrollPos: ${scrollPosition}; --scrollPosDeg: ${scrollPositionDeg};`"

        class="dev-list__simplebar"
        data-simplebar-direction="rtl"
        data-simplebar-auto-hide="false">
        <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio ONE</button>
        <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio TWO</button>
        <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio THRE</button>
        <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio FOUR</button>
        <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio FIVE</button>
      </simplebar>




    </div>
    <div class="dev-nav">
      <a href="" class="dev-nav__item">about</a>
      <a href="" class="dev-nav__item">design</a>

    </div>


    <div class="dev-modal" v-if="isModalVisible">
      <button @click="closeModal()" class="dev-modal__close">X</button>

      <h1 class="dev-modal__title">{{ this.currentModalProject.title }}</h1>

      <div class="dev-modal__body">
        <p v-for="paragraph in this.currentModalProject.description">{{ paragraph }}</p>
      </div>

      <silent-box :preview-count="3" :gallery="this.currentModalProject.images"></silent-box>

      <a href="#">
        <img src="../assets/images/github.svg" class="dev-modal__github" alt="">
      </a>

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

      projectList: {
        project_one: {
          title: "This Portfolio ONE",
          description: [
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Ab odio provident quo voluptate. Doloribus et fugit officiis quaerat reprehenderit sunt?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Debitis eaque enim est excepturi facilis illum repellat veniam? Alias blanditiis cum dolore, quae qui quibusdam sequi. Architecto debitis dolor ipsa molestiae nobis repellat repudiandae, sequi ut!\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, eum exercitationem impedit laudantium officiis voluptatum?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, eum exercitationem impedit laudantium officiis voluptatum?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, eum exercitationem impedit laudantium officiis voluptatum?\n",
            "Lorem ipsum dolor sit amet, consectetur adipisicing elit. Error, eum exercitationem impedit laudantium officiis voluptatum?\n"
          ],
          images: [
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
            {
              src: require('assets/images/tester1.png'),
              srcSet: require('assets/images/tester1.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
            {
              src: require('assets/images/tester2.png'),
              srcSet: require('assets/images/tester2.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '1600px',
            },
            {
              src: require('assets/images/tester3.png'),
              srcSet: require('assets/images/tester3.png'),
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

  computed: {

  }

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
.dev-container, .dev-item, .dev-nav-tablet {
  color: white;
  font-family: "Blue Screen Personal Use", "Consolas", Courier, monospace;
  text-shadow: 0px 0px 10px #000000;
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
  padding-top: 20px;
}

.dev-nav__item {
  font-size: 2em;
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

  .dev-modal__body {

    padding-top: 10px;

    width: 70vw;

    font-family: "IBM Plex Mono", monospace;
    font-weight: 300;
    font-size: .8em;

    max-height: 65%;
    overflow: auto;
    margin-bottom: 20px;

    p {
      margin-bottom: 15px;
    }
  }

}

.dev-nav-tablet {
  display: none;
}

/* BreakPoints */
$breakpoint-tablet: 768px;
$breakpoint-mobile: 501px;

// ====  Dev media queries - ON TABLET ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-mobile) {

  // =  Dev Background - tablet
  .dev-container {

  }

  // =  Dev Text Defaults - tablet
  .dev-container, .dev-item {

  }

  .dev-title {
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

    padding: 5vh 9vw 7vh 9vw;

    .dev-nav-tablet__item {
      font-size: 1.5em;
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

    .dev-modal__body {


    }
  }

  .dev-list__simplebar {
    height: 70vh;
    direction: rtl;
  }

}



// ====  Dev media queries - ON DESKTOP ==== ==== ==== ==== ==== ==== ==== ==== ==== ====
@media (min-width: $breakpoint-tablet) {

  // =  Dev Background - desktop
  .dev-container {

  }

  // =  Dev Text Defaults - desktop
  .dev-container, .dev-item {

  }

  .dev-title {
      color: lime;
  }

  // =  Dev List - desktop
  .dev-list {

  }

  // =  Dev List Item - desktop
  .dev-item {


    &:last-child {

    }
  }

  // =  Dev Nav - desktop
  .dev-nav {
  }

  .dev-nav__item {

  }

  // =  Dev Modal - desktop
  .dev-modal {


    .dev-modal__close {

    }

    .dev-modal__title {

    }

    .dev-modal__github {

    }

    .dev-modal__body {


    }

  }

}


</style>


<style>

/* ================ ================ ================  SIMPLEBAR STYLES ================ ================ ================ */

/*
.simplebar-scrollbar  {
  background-image: url("../assets/images/scroll-thumb-arrow.svg");
  mix-blend-mode: exclusion;
  background-repeat: no-repeat;
  background-size: contain;

  transition: all .5s;
}
*/

.simplebar-scrollbar > * {
  box-sizing: border-box;
}

.simplebar-scrollbar{
  box-sizing: border-box;

  position: relative;
  width: 60px;
  right: -30px;

  mix-blend-mode: exclusion;
}

.simplebar-scrollbar:before {

  top: calc(var(--scrollPos) - (var(--scrollPos) * .21 )) !important;

  background-image: url("./assets/images/scroll-thumb-arrow2.svg") !important;
  background-repeat: no-repeat;
  background-position-x: center;

  mix-blend-mode: exclusion;

  transform: rotate( calc(var(--scrollPosDeg) * -1) ) !important;
  transform-origin: 50% 50%;

  position: absolute !important;
  width: 100% !important;
  height: 75px !important;

  margin-top: 5px;

  left: 0;
  right: 0;

  z-index: -1 !important;

  border-radius: 0;
  opacity: 1 !important;

}


.simplebar-track {
  padding: 0 30px 0 30px;
  margin: 0 30vw 0 9vw;
  background-image: url("../assets/images/scroll-bg.png");
  background-size: contain;
}


/* ================ ================ ================  SILENTBOX STYLES ================ ================ ================ */

#silentbox-gallery {
  display: flex;
  justify-content: space-around;
  max-width: 100%;
  overflow: hidden;
  padding-left: 20px;
}

.silentbox-item {
  margin-right: 20px;

}

.silentbox-item:nth-child(2) {
}

.silentbox-item > img {
  height: 211px;
  max-width: 145px;
  object-fit: cover;
}

</style>
