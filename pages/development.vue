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
      <div class="dev-modal__body">
        <h1 class="dev-modal__title">{{ this.currentModalProject.title}}</h1>
        <a href="#" >
          <img src="../assets/images/github.svg" class="dev-modal__github" alt="">
        </a>
      </div>
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
          description: "this is the description of project ONE "

        },
        project_two: {
          title: "This Portfolio TWO",
          description: "this is the description of project TWOO"

        },
        project_three: {
          title: "This Portfolio THREE",
          description: "this is the description of project THREE"

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
    margin: 20px;
  }

  .dev-modal__body {
    padding: 20px;

    .dev-modal__title {
      transform: rotate(90deg);
      position: absolute;
      top: 113px;
      right: -37px;
    }

    .dev-modal__github {
      position: absolute;
      top: 210px;
      left: 273px;
    }
  }
}


/* BreakPoints */
$breakpoint-tablet: 768px;
$breakpoint-mobile: 501px;
</style>
