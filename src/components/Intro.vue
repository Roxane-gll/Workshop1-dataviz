<template>
  <section id="intro">

    <img src="../assets/img/backgroundIntro.svg" alt="background" class="background">

    <div class="wrapper">

      <p>C'est parti</p>

      <h3>Commencer</h3>

      <div>

        <img src="../assets/img/arrowIntro.svg" alt="arrow">

        <h3>l'experience</h3>

      </div>

    </div>

  </section>
</template>

<script>
import allStories from '../assets/stories.json'

export default {
  name: 'Intro',
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

