<template>
  <div id="app">
    <Header :page="currentPage" :current-story="story" :story="getCurrentStory" @newPage="changePage"></Header>
    <component :story="getCurrentStory" :is="getCurrentPage"></component>
    <Footer :story="getCurrentStory" :currentPage="currentPage" :nbPages="Object.keys(pages).length" @newPage="changePage"></Footer>
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
