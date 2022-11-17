<template>
  <div id="app">
    <Header :page="currentPage" :current-story="currentStory" :story="getCurrentStory" @newPage="changePage"></Header>
    <component :story="getCurrentStory" :is="getCurrentPage"></component>
    <Footer :story="getCurrentStory"></Footer>
  </div>
</template>

<script>
import Stories from './pages/Stories.vue'
import allStories from '../assets/stories.json'
import Graph from './pages/Graph.vue'
import Presentation from './pages/Presentation.vue'
import Header from './Header.vue'
import Footer from './Footer.vue'

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
      currentStory: this.story,
      currentPage: 1,
      pages: {
        1: Presentation,
        2: Stories,
        3: Graph
      }
    }
  },
  computed: {
    getCurrentPage() {
      return this.pages[this.currentPage]
    },
    getCurrentStory() {
      return this.allStories.find((story) => story.id === this.currentStory)
    }
  },
  methods: {
    changeStory(newStoryId) {
      this.currentPage = 1
      this.currentStory = newStoryId
    },
    changePage(newPage) {
      if (!this.pages[this.currentPage + newPage]) {
        return
      }
      this.currentPage += newPage
    }
  }
}
</script>

<style scoped>

</style>
