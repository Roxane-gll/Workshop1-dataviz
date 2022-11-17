<template>
  <section id="storyTwo" :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div class="left-part">

        <p v-html="story.content.storyTwo.p1" ></p>

      </div>

      <div class="right-part">

      </div>

    </div>

  </section>
</template>

<script>
export default {
  name: 'StoryTwo',
  props: {
    story:{
      type: Object
    }
  }

}
</script>

<style scoped>
</style>
