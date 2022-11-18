<template>
    <section :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div class="left-part">

        <p v-html="story.time" ></p>
        {{startForm.time}}

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
  }
  
}
</script>
