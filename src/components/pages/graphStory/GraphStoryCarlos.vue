<template>
  <div class="hello">

    <div class="data-wrapper">
      <h5 class="data">{{ story.graph.g1[gaphCountry].data }}</h5>
      <img class="imgGraph" :src="require(`@/assets/img/graphCarlos/${story.graph.g1[gaphCountry].img}`)">
    </div>

    <p v-html="story.graph.g1[gaphCountry].phrase" class="phrase"></p>

    <hr>

    <div class="button-wrapper">
      <div :class="gaphCountry === key ? 'button active' : 'button'" v-for="(values, key) in story.graph.g1" :key="key" @click="switchCountry(key)">
        {{ key }}
      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: 'GraphStoryCarlos',
  props: {
    story: {
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
