<template>
  <div class="hello">

    <div style="display: flex;">
        <div v-for="(value, person) in story.graph.g1" :key="person">
            <div v-if="seeSituation[person]">
                <img :src="require(`@/assets/img/${value}`)">
            </div>
            <img :src="require(`@/assets/img/graphDevi/${person}.svg`)" @click="newSeeSituation(person)">
        </div>
    </div>

    <p v-html="story.graph.g1Phrase"></p>
  </div>
</template>

<script>
export default {
  name: 'GraphStoryDevi',
  props: {
    story:{
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
