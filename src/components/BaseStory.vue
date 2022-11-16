<template>
  <div>
    <button @click="changePage(-1)">←</button>
    <button @click="changePage(1)">→</button>

    <component :story="getCurrentStory" :is="getCurrentPage"></component>

    <ChangeStoryButton :currentStory="story" @newStory="changeStory"></ChangeStoryButton>
  </div>
</template>

<script>
import Stories from './pages/Stories.vue'
import allStories from '../assets/stories.json'
import Graph from './pages/Graph.vue'
import ChangeStoryButton from './ChangeStoryButton.vue'

export default {
  name: 'BaseStory',
  components: {ChangeStoryButton},
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
    }
  }
}
</script>

<style scoped>

</style>
