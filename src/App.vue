<template>
  <div>
    <Transition mode="out-in">
      <component :story="currentStory" :is="getCurrentComponent" :startForm="startForm" @newStory="changeStory" @startForm="saveForm" @home="homePage" @restart="restart" @intro="intro"></component>
    </Transition>
  </div>
</template>


<script src="https://unpkg.com/@lottiefiles/lottie-player@1.5.7/dist/lottie-player.js"></script>
<script src="./assets/js/main.js"></script>

<script>
import Intro from './components/Intro.vue'
import allStories from './assets/stories.json'
import BaseStory from './components/BaseStory.vue'
import StorySelector from './components/StorySelector.vue'
import StartForm from './components/StartQuestion.vue'

export default {
  name: 'App',
  data() {
    return {
      allStories,
      currentStory: 1,
      currentComponent: "Intro",
      components: {
        "Intro": Intro,
        "Start": StartForm,
        "Home": StorySelector,
        "Story": BaseStory
      },
      startForm: {}
    }
  },
  computed: {
    getCurrentComponent() {
      return this.components[this.currentComponent]
    }
  },
  methods: {
    changeStory(newStoryId) {
      this.currentStory = newStoryId
      this.currentComponent = "Story"
    },
    saveForm(model) {
      this.startForm = model
      this.currentComponent = "Home"
    },
    homePage() {
      this.currentComponent = "Home"
    },
    restart() {
      this.currentComponent = "Start"
    },
    intro() {
      this.currentComponent = "Intro"
    }
  }
}

</script>

<style lang="css">

@import './assets/scss/style.css';
.v-enter-active {
  animation: bounce-in 0.5s;
}
.v-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
</style>
