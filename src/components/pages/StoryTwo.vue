<template>
  <section id="storyTwo" :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div class="left-part">

        <p v-html="story.content.storyTwo.p1" ></p>

        <p class="p2" v-html="story.content.storyTwo.p2" ></p>

      </div>

      <div class="right-part">
        <GraphStoryOlivier v-if="story.id === 1" :story="story"></GraphStoryOlivier>
        <GraphStoryFigg v-else-if="story.id === 3" :story="story"></GraphStoryFigg>
      </div>

    </div>

  </section>
</template>

<script>
import GraphStoryOlivier from './graphStory/GraphStoryOlivier.vue'
import GraphStoryFigg from './graphStory/GraphStoryFigg.vue'

export default {
  name: 'StoryTwo',
  components: {GraphStoryOlivier, GraphStoryFigg},
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
