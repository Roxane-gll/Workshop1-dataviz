<template>
    <section :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div>
        <div v-for="(title, question) in questionTitle" :key="title" @click="changeGraph(question)">
          {{title}}
        </div>
      </div>
      <div>
        <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)">
        {{startForm[currentGraph]}}
      </div>

      <div>
        <img :src="require(`@/assets/img/${story.style.iconChildren}`)">
        {{story[currentGraph]}}
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
  },
  data() {
    return {
      questionTitle: {
        time:"Temps",
        distance: "Distance"
      },
      currentGraph: "time"
    }
  },
  methods: {
    changeGraph(graph) {
      this.currentGraph = graph
    }
  }
}
</script>
