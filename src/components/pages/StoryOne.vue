<template>
  <section id="storyOne" :style="{ background: story.style.colors.background }" :class="story.name">

    <div class="top-part">

      <p class="p1" v-html="story.content.storyOne.p1"></p>

      <p class="p2" v-html="story.content.storyOne.p2"></p>

      <p class="p3" v-html="story.content.storyOne.p3"></p>

    </div>

    <div class="bottom-part">

      <p class="p1" v-html="story.content.storyOne.p4"></p>

      <p class="p2" v-html="story.content.storyOne.p5"></p>

    </div>

    <img :src="require(`@/assets/img/${story.style.assetStoryOne}`)" alt="Country" class="asset">

  </section>
</template>

<script>
export default {
  name: 'StoryOne',
  props: {
    story:{
      type: Object
    }
  }
  
}
</script>

<style scoped>
</style>
