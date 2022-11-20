<template>

  <div class="graph-wrapper">

    <div class="button-wrapper">

      <button :class="graphCountry === key ? 'button active' : 'button'" v-for="(values, key) in story.graph.g1"
              :key="key" @click="switchCountry(key)">{{ key }}
      </button>

    </div>

    <div class="date-wrapper">

      <div v-for="(values, date) in story.graph.g1[graphCountry]" :key="date" @click="switchYear(date)" :class="gaphYear === date ? 'date active' : 'date'">
        {{ date }}
      </div>

    </div>

    <div class="data-wrapper">

      <div class="data" v-for="(value, index) in story.graph.g1[graphCountry][gaphYear]" :key="index">

        <img :src="value ? require('@/assets/img/school.svg') : require('@/assets/img/schoolDestroyed.svg')"
             class="imgSchool" alt="school">

      </div>

    </div>

    <p class="phrase">{{ story.graph.g1Phrase }}</p>

  </div>

</template>

<script>
export default {
  name: 'GraphStoryOlivier',
  props: {
    story: {
      type: Object
    }
  },
  data() {
    return {
      gaphYear: "2017",
      graphCountry: "Mali"
    }
  },
  methods: {
    switchYear(year) {
      this.gaphYear = year
    },
    switchCountry(country) {
      this.graphCountry = country
    }
  }

}
</script>
