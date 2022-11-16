<template>
  <div style="display:flex">
    <div @click="sendHome">Home</div>

    <template v-for="story in allStories">
      <div :key="story.id" @click="changeStory(story.id)" >
          <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="Icon of the children" :class="story.id === currentStory ?'changeStoryButton selectedStory': 'changeStoryButton'">
      </div>
    </template>
  </div>
</template>

<script>
import allStories from '../assets/stories.json'

export default {
  name: 'ChangeStoryButtons',
  props: {
      currentStory: {
          type:Number
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
.changeStoryButton {
    width: 50px;
    border-radius: 100%;
}
.selectedStory {
    background-color: red;
}
</style>
