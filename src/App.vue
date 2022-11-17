<template>
  <div>
    <component :story="currentStory" :is="getCurrentComponent" @newStory="changeStory" @startForm="saveForm" @home="homePage" @restart="restart"></component>
  </div>
</template>

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
    }
  }
}
</script>

<style lang="css">

@import './assets/scss/style.css';

</style>
