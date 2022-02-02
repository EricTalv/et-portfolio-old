<template>
  <main class="dev-container">
    <div class="dev-title">
      DEVELOPMENT
    </div>
    <div class="dev-list">

      <button @click="showModal(projectList.project_one)" class="dev-item">This Portfolio ONE</button>
      <button @click="showModal(projectList.project_two)" class="dev-item">This Portfolio TWO</button>
      <button @click="showModal(projectList.project_three)" class="dev-item">This Portfolio THREE</button>

    </div>
    <div class="dev-nav">
      <a  href="" class="dev-nav__item">about</a>
      <a  href="" class="dev-nav__item">design</a>

    </div>


    <div class="dev-modal" v-if="isModalVisible">
      <button @click="closeModal()" class="dev-modal__close">X</button>

      <h1 class="dev-modal__title">{{ this.currentModalProject.title}}</h1>

      <div class="dev-modal__body">
        <p v-for="paragraph in this.currentModalProject.description">{{ paragraph }}</p>
      </div>

      <silent-box :gallery="this.currentModalProject.images"></silent-box>

      <a href="#" >
        <img src="../assets/images/github.svg" class="dev-modal__github" alt="">
      </a>

    </div>


  </main>
</template>

<script>
export default {
  name: "development",

  data () {
    return {
      isModalVisible: false,
      currentModalProject: null,

      projectList: {
        project_one: {
          title: "This Portfolio ONE",
          description: [
            "This is some text one",
            "This is some text Three",
            "This is some text Two"
          ],
          images: [
            {
              src: require('assets/images/placeholder.png'),
              srcSet: require('assets/images/placeholder.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '150px',
            },
            {
              src: require('assets/images/big-bg.png'),
              srcSet: require('assets/images/big-bg.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '150px',
            },
            {
              src: require('assets/images/mobile-bg.png'),
              srcSet: require('assets/images/mobile-bg.png'),
              description: 'Sunken dreams II. by Arbebuk',
              thumbnailWidth: '150px',
            }
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
    }
  }
}
</script>

<style lang="scss" scoped>


// ====  ON MOBILE
// =  Dev Background
.dev-container {
  width: 100%;

  background-color: black;
  background-image: url("../assets/images/mobile-bg.png");
  background-repeat: no-repeat;
  background-position: center;

  background-size: 100% 1500px;

  display: flex;
  flex-flow: column;
  padding-top: 5vh;
}

// =  Dev Text Defaults
.dev-container, .dev-item {
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

// =  Dev List
.dev-list {
  width: 100%;
  height: 56vh;

  overflow-y: auto;


}

// =  Dev List Item
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

// =  Dev Nav
.dev-nav {
  display: flex;
  justify-content: space-around;
  padding-top: 20px;
}

.dev-nav__item {
  font-size: 2em;
}

// =  Dev Modal
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
    top:72px;
    right:22px;
  }

  .dev-modal__body {

    padding-top: 10px;
    padding-right: 30px;

    font-family: "IBM Plex Mono", monospace;
    font-weight: 300;
    font-size: .8em;

    p {
      margin-bottom: 15px;
    }
  }

}



#silentbox-gallery {
  position: absolute;
  display: flex;
  bottom: 124px;
  left: 0;

  .silentbox-item {
    border: 5px solid red !important;
  }


}



/* BreakPoints */
$breakpoint-tablet: 768px;
$breakpoint-mobile: 501px;
</style>
