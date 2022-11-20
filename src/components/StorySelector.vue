<template>
  <div id="app">
    <header>
      <div @click="sendStart" class="goHome-wrapper" style="background: #F8F3EE">
          <img src="../assets/img/cross.svg" alt="home button">
      </div>
    </header>

    <div id="choose-children-wrapper">
      <template v-for="story in allStories">
        <div class="children-wrapper" :key="story.id" @click="chooseStory(story.id)">

          <img :src="require(`@/assets/img/${story.style.backgroundChooseChildren}`)" alt="background Children" class="backgroundChooseChildren">

          <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="Icon of the children" class="iconChildren">

          <div class="info-children" :style="{ color: story.style.colors.presentation }">

            <h5 class="history">L'histoire de</h5>

            <h2 class="name">{{ story.name }}</h2>

            <div class="country-wrapper">
              <h3 class="country">{{ story.country }}</h3>
              <img :src="require(`@/assets/img/${story.style.arrowChildren}`)" alt="Arrow of the children">
            </div>

          </div>
        </div>
      </template>
    </div>

  </div>
</template>

<script>
import allStories from '../assets/stories.json'

export default {
  name: 'StorySelector',
  props: {
      story: {
          type:Number
      }
  },
  data() {
    return {
      allStories
    }
  },
  methods: {
    chooseStory(newStoryId) {
        this.$emit('newStory', newStoryId)
    },
    sendStart() {
      this.$emit('restart')
    }
  }
}
</script>

