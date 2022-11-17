<template>
  <div>
    <component :story="currentStory" :is="getCurrentComponent" @newStory="changeStory" @startForm="saveForm" @home="homePage"></component>
  </div>
</template>

<script>
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
      currentComponent: 1,
      components: {
        1: StartForm,
        2: StorySelector,
        3: BaseStory
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
      this.currentComponent = 3
    },
    saveForm(model) {
      this.startForm = model
      this.currentComponent = 2
    },
    homePage() {
      this.currentComponent = 2
    }
  }
}
</script>

<style lang="css">

@import './assets/scss/style.css';

</style>
