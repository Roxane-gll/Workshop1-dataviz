<template>
  <section id="intro" @click="sendToForm">

    <img src="../assets/img/backgroundIntro.svg" alt="background" class="background">

    <div class="wrapper">

      <p>C'est parti</p>

      <h3>Commencer</h3>

      <div>

        <h3>l'experience</h3>

        <img src="../assets/img/arrowIntro.svg" alt="arrow">

      </div>

    </div>

    <div class="logo-wrapper">

      <img src="../assets/img/gobelins.svg" alt="logo gobelins">

      <img src="../assets/img/lecole.svg" alt="logo gobelins">

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
    sendToForm() {
      this.$emit('restart')
    }
  }
}
</script>

