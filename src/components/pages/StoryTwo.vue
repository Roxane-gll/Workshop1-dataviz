<template>
  <section id="storyTwo" :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div class="left-part">

        <p v-html="story.content.storyTwo.p1" ></p>

      </div>

      <div class="right-part">
        <div style="display:flex;">
          <div v-for="(values, key) in story.graph.g1" :key="key" @click="switchYear(key)">
            {{key}}
          </div>
        </div>

        <div>
          <img v-for="(value, index) in story.graph.g1[gaphYear]" :key="index" :src="value ? require('@/assets/img/school.svg') : require('@/assets/img/schoolDestroyed.svg')" class="imgSchool">
        </div>
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
  },
  data() {
    return {
      gaphYear: "2018"
    }
  },
  methods: {
    switchYear(year) {
      this.gaphYear = year
    }
  }
}
</script>

<style scoped>
.imgSchool {
  width: 20px;
}
</style>
