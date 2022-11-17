<template>
  <div class="hello">
    <div style="display:flex;">
          <div v-for="(values, key) in story.graph.g1" :key="key" @click="switchYear(key)">
            {{key}}
          </div>
        </div>

        <div>
          <img v-for="(value, index) in story.graph.g1[gaphYear]" :key="index" :src="value ? require('@/assets/img/school.svg') : require('@/assets/img/schoolDestroyed.svg')" class="imgSchool">
        </div>
        <p>{{story.graph.g1Phrase}}</p>
        <p v-if="gaphYear === '2019'"> {{story.graph.g1PhraseEnd}}</p>
  </div>
</template>

<script>
export default {
  name: 'GraphStoryOlivier',
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
