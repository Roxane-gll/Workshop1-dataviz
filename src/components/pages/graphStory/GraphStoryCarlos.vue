<template>
  <div class="hello">
    <div style="display:flex;">
          <div v-for="(values, key) in story.graph.g1" :key="key" @click="switchCountry(key)">
            {{key}}
          </div>
        </div>

        <div>
          <img :src="require(`@/assets/img/graphCarlos/${story.graph.g1[gaphCountry].img}`)">
        </div>

        <p v-html="story.graph.g1[gaphCountry].phrase"></p>
  </div>
</template>

<script>
export default {
  name: 'GraphStoryCarlos',
  props: {
    story:{
      type: Object
    }
  },
  data() {
    return {
      gaphCountry: "Mali"
    }
  },
  methods: {
    switchCountry(country) {
      this.gaphCountry = country
    }
  }
  
}
</script>
