<template>
  <div id="app">
    <Header :current-story="story" :story="getCurrentStory" @newStory="changeStory" @home="sendHome"></Header>
    <component :story="getCurrentStory" :is="getCurrentPage"></component>
    <Footer :story="getCurrentStory" :currentPage="currentPage" :nbPages="Object.keys(pages).length" @newPage="changePage"></Footer>
  </div>
</template>

<script>

import allStories from '../assets/stories.json'
import Header from './pages/fixedAssets/Header.vue'
import Footer from './pages/fixedAssets/Footer.vue'
import Presentation from './pages/Presentation.vue'
import StoryOne from './pages/StoryOne.vue'
import StoryTwo from './pages/StoryTwo.vue'
import Graph from './pages/Graph.vue'

export default {
  name: 'BaseStory',
  components: {Header, Footer},
  props: {
      story: {
          type:Number
      }
  },
  data() {
    return {
      allStories,
      currentPage: 1,
      pages: {
        1: Presentation,
        2: StoryOne,
        3: StoryTwo,
        4: Graph
      }
    }
  },
  computed: {
    getCurrentPage() {
      return this.pages[this.currentPage]
    },
    getCurrentStory() {
      return this.allStories.find((story) => story.id === this.story)
    }
  },
  methods: {
    changeStory(newStoryId) {
      this.currentPage = 1
      this.$emit('newStory', newStoryId)
    },
    changePage(newPage) {
      if (!this.pages[this.currentPage + newPage]) {
        return
      }
      this.currentPage += newPage
    },
    sendHome() {
      this.$emit('home')
    }
  }
}
</script>

<style scoped>

</style>
