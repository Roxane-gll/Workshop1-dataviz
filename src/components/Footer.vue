<template>
  <div id="app">
    <footer>

      <div class="arrow prev" :style="{ background: story.style.colors.arrow, color: story.style.colors.arrow }">
        <img src="../assets/img/arrow.svg" alt="arrow">
      </div>

      <div class="arrow next" :style="{ background: story.style.colors.arrow, color: story.style.colors.arrow }">
        <img src="../assets/img/arrow.svg" alt="arrow">
      </div>

    </footer>
  </div>
</template>

<script>
import allStories from '../assets/stories.json'

export default {
  name: 'Footer',
  props: {
    currentStory: {
      type:Number
    },
    story: {
      type: Object
    }
  },
  data() {
    return {
      allStories,
    }
  },
  methods: {
  }
}
</script>

<style scoped>

</style>
