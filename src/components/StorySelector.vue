<template>
  <div>
    <div id="choose-children-wrapper">
      <template v-for="story in allStories">
        <div class="children-wrapper" :key="story.id" @click="chooseStory(story.id)">

          <img :src="require(`@/assets/img/${story.style.backgroundChooseChildren}`)" alt="background Children" class="backgroundChooseChildren">

          <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="Icon of the children" class="iconChildren">

          <div class="info-children" :style="{ color: story.style.colors.presentation }">

            <h5 class="history">L'histoire de</h5>

            <h2 class="name">{{ story.name }}</h2>

            <div class="country-wrapper">
              <img :src="require(`@/assets/img/${story.style.arrowChildren}`)" alt="Arrow of the children">

              <h3 class="country">{{ story.country }}</h3>
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
    }
  }
}
</script>

