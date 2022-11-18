<template>
    <section :style="{ background: story.style.colors.background }">

    <h2 class="title" v-html="story.content.storyTwo.title" :style="{ color: story.style.colors.arrow }"></h2>

    <div class="wrapper">

      <div>
        <div v-for="(title, question) in questionTitle" :key="title" @click="changeGraph(question)">
          {{title}}
        </div>
      </div>
      <div v-if="currentGraph === 'time'">
        <div>
          <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)">
          {{startForm[currentGraph]}}
          <div v-for="clock in getClockNumber(getTimeInMinute(startForm[currentGraph]))" :key="clock">
            {{clock}}
          </div>
        </div>

        <div>
          <img :src="require(`@/assets/img/${story.style.iconChildren}`)">
          {{story[currentGraph]}}
          <div v-for="clock in getClockNumber(getTimeInMinute(story[currentGraph]))" :key="clock">
            {{clock}}
          </div>
        </div>
      </div>

      <div v-if="currentGraph === 'distance'">
        <div>
          <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)">
          {{startForm[currentGraph]}} km
        </div>

        <div>
          <img :src="require(`@/assets/img/${story.style.iconChildren}`)">
          {{story[currentGraph]}}
        </div>
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
    },
    getClockNumber(time) {
      const timeInHours = time / 60
      let clockTime = timeInHours
      const arrayClock = []
      for (let i = 1; i < Math.round(timeInHours); i++) {
        arrayClock.push(1)
      }
      arrayClock.push(clockTime - arrayClock.length)
      return arrayClock
    },
    getTimeInMinute(time) {
      let fullTimeInMinute = parseInt(time)
      if (time.includes('h')) {
        const nbHours = time.split('h')
        const hoursInMinute = parseInt(nbHours[0]) * 60
        fullTimeInMinute = parseInt(nbHours[1]) + hoursInMinute
      }
      
      return fullTimeInMinute
    }
  }
}
</script>
