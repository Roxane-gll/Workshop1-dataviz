<template>
  <section id="storyTwo" :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div class="left-part">

        <p v-html="story.content.storyTwo.p1" ></p>

      </div>

      <div class="right-part">
        <GraphStoryOlivier v-if="story.id === 1" :story="story"></GraphStoryOlivier>
      </div>

    </div>

  </section>
</template>

<script>
import GraphStoryOlivier from './GraphStoryOlivier.vue'

export default {
  name: 'StoryTwo',
  components: {GraphStoryOlivier},
  props: {
    story:{
      type: Object
    }
  }
}
</script>

<style scoped>
.imgSchool {
  width: 20px;
}
</style>
