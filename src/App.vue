<template>
  <div id="app">
    <button @click="changePage(-1)">←</button>
    <button @click="changePage(1)">→</button>
    <component :story="getCurrentStory" :is="getCurrentPage"></component>

    <template v-for="story in allStories">
      <button :key="story.id" @click="changeStory(story.id)">{{story.name}}</button>
    </template>
  </div>
</template>

<script>
import Stories from './components/Stories.vue'
import allStories from './assets/stories.json'
import Graph from './components/Graph.vue'

export default {
  name: 'App',
  data() {
    return {
      allStories,
      currentStory: 1,
      currentPage: 1,
      pages: {
        1: Stories,
        2: Graph
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
