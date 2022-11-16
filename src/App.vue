<template>
  <div id="app">
    <!--<button @click="changePage(-1)">←</button>
    <button @click="changePage(1)">→</button>-->
    <component :story="getCurrentStory" :is="getCurrentPage"></component>

    <div id="choose-children-wrapper">

      <template v-for="story in allStories">

        <div class="children-wrapper" :key="story.id" @click="changeStory(story.id)">

          <img :src="require(`./assets/img/${story.style.backgroundChooseChildren}`)" alt="background Children" class="backgroundChooseChildren">

          <img :src="require(`./assets/img/${story.style.iconChildren}`)" alt="Icon of the children" class="iconChildren">

          <div class="info-children">

            <h5 class="history">L'histoire de</h5>

            <h2 class="name">{{ story.name }}</h2>

            <div class="country-wrapper">

              <img :src="require(`./assets/img/${story.style.arrowChildren}`)" alt="Arrow of the children">

              <h3 class="country">{{ story.country }}</h3>

            </div>


          </div>

        </div>

      </template>

    </div>

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

<style lang="css">

@import './assets/scss/style.css';

</style>
