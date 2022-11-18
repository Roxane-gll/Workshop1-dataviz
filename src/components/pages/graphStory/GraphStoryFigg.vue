<template>
  <div class="hello">

    <div class="button-wrapper">
      <div :class="gaphCountry === key ? 'button active' : 'button'" v-for="(values, key) in story.graph.g1" :key="key"
           @click="switchCountry(key)">
        {{ key }}
      </div>
    </div>

    <hr>

    <div class="data-wrapper">

      <img class="teacher" :src="require('@/assets/img/schoolImg/teacher.svg')" alt="teacher">

      <div class="students-wrapper">
        <img v-for="(value, index) in story.graph.g1[gaphCountry]" :key="index" :src="require(`@/assets/img/schoolImg/${value}.svg`)" class="imgSchool" alt="students">
      </div>

    </div>

    <p class="phrase">En {{ gaphCountry }}, un professeur donne cours à {{ story.graph.g1[gaphCountry].length }} élèves
      en moyenne.</p>

  </div>
</template>

<script>
export default {
  name: 'GraphStoryFigg',
  props: {
    story: {
      type: Object
    }
  },
  data() {
    return {
      gaphCountry: "France"
    }
  },
  methods: {
    switchCountry(country) {
      this.gaphCountry = country
    }
  }

}
</script>
