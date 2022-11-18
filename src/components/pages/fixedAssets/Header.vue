<template>
  <div id="app">
    <header>

      <div @click="sendHome" class="goHome-wrapper" :style="{ background: story.style.colors.goHome }">
        <img :src="require(`@/assets/img/${story.style.home}`)" alt="home button">
      </div>

      <div class="children-wrapper">

        <template v-for="story in allStories">
          <div :key="story.id" @click="changeStory(story.id)" class="children" :class="story.id === currentStory ?'selectedStory': ''">
            <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="Icon of the children">
          </div>
        </template>

      </div>

    </header>
  </div>
</template>

<script>
import allStories from '@/assets/stories.json'

export default {
  name: 'Header',
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
    changeStory(newStoryId) {
      this.$emit('newStory', newStoryId)
    },
    sendHome() {
      this.$emit('home')
    }
  }
}
</script>

<style scoped>

</style>
