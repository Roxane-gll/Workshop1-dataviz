<template>
    <section :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div>
        <div v-for="(userValue, question) in startForm" :key="question">
          {{userValue}}
          {{question}}
        </div>
      </div>

    </div>

  </section>
</template>

<script>
export default {
  name: 'Graph',
  props: {
    story:{
      type: Object
    },
    startForm: {
      type: Object
    }
  },

}
</script>
