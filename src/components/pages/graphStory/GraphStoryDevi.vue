<template>
  <div class="graph-wrapper">

    <div class="data-wrapper">
      <div v-for="(value, person) in story.graph.g1" :key="person" class="data">
        <div class="situation">
          <img :src="require(`@/assets/img/${value}`)"  v-if="seeSituation[person]" alt="situation">
        </div>
        <img :src="require(`@/assets/img/graphDevi/${person}.svg`)" @click="newSeeSituation(person)" class="girl" alt="girl">
      </div>
    </div>

    <p v-html="story.graph.g1Phrase" class="phrase"></p>

  </div>
</template>

<script>
export default {
  name: 'GraphStoryDevi',
  props: {
    story: {
      type: Object
    }
  },
  data() {
    return {
      seeSituation: {
        fille1: false,
        fille2: false,
        fille3: false
      }
    }
  },
  methods: {
    newSeeSituation(person) {
      this.seeSituation[person] = !this.seeSituation[person]
    }
  }

}
</script>
