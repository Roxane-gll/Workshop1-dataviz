<template>
  <div id="app">
    <Header :current-story="story" :story="getCurrentStory" @newStory="changeStory" @home="sendHome"></Header>

    <Transition mode="out-in">
      <component :story="getCurrentStory" :startForm="startForm" :is="getCurrentPage"></component>
    </Transition>

    <Footer :story="getCurrentStory" :currentPage="currentPage" :nbPages="Object.keys(pages).length"
            @newPage="changePage"></Footer>
    <audio class="audioBackground" :src="require(`@/assets/sounds/${getAudio}`)" autoplay></audio>
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
      type: Number
    },
    startForm: {
      type: Object
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
    },
    getAudio() {
      return this.getCurrentStory.sounds.background
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
