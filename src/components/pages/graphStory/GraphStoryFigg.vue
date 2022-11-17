<template>
  <div class="hello">
    <div style="display:flex;">
          <div v-for="(values, key) in story.graph.g1" :key="key" @click="switchCountry(key)">
            {{key}}
          </div>
        </div>

        <div>
            <img :src="require('@/assets/img/schoolImg/teacher.svg')">
        </div>

        <div>
          <img v-for="(value, index) in story.graph.g1[gaphCountry]" :key="index" :src="require(`@/assets/img/schoolImg/${value}.svg`)" class="imgSchool">
        </div>
  </div>
</template>

<script>
export default {
  name: 'GraphStoryFigg',
  props: {
    story:{
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
