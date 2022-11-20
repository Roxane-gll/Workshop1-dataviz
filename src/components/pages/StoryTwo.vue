<template>

  <div>

    <section id="storyTwo" :style="{ background: story.style.colors.background }" :class="story.name">

      <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

      <div class="wrapper">

        <div class="left-part">

          <p v-html="story.content.storyTwo.p1" ></p>

          <p class="p2" v-html="story.content.storyTwo.p2" ></p>

          <p class="additionalPhrase" v-if="story.id === 2">Clique sur les jeunes filles pour<br>découvrir qui se rend à l’école ! </p>

          <p class="additionalPhrase" v-if="story.id === 1" v-html="additionalPhraseOlivier"></p>

        </div>

      </div>

      <div class="graph-wrapper">
        <GraphStoryOlivier v-if="story.id === 1" :story="story" @phrase="phrase"></GraphStoryOlivier>
        <GraphStoryDevi v-else-if="story.id === 2" :story="story"></GraphStoryDevi>
        <GraphStoryFigg v-else-if="story.id === 3" :story="story"></GraphStoryFigg>
        <GraphStoryCarlos v-else-if="story.id === 4" :story="story"></GraphStoryCarlos>
      </div>

    </section>

    <audio :src="require(`@/assets/sounds/${story.sounds.two}`)" autoplay></audio>

  </div>

</template>

<script>
import GraphStoryOlivier from './graphStory/GraphStoryOlivier.vue'
import GraphStoryFigg from './graphStory/GraphStoryFigg.vue'
import GraphStoryCarlos from './graphStory/GraphStoryCarlos.vue'
import GraphStoryDevi from './graphStory/GraphStoryDevi.vue'

export default {
  name: 'StoryTwo',
  components: {GraphStoryOlivier, GraphStoryFigg, GraphStoryCarlos, GraphStoryDevi},
  props: {
    story:{
      type: Object
    }
  },
  data() {
    return {
      additionalPhraseOlivier: null
    }
  },
  methods: {
    phrase(phrase) {
      this.additionalPhraseOlivier = phrase
    }
  }
}
</script>

<style scoped>
</style>
