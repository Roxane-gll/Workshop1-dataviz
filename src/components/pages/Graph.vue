<template>

    <section id="graph" :style="{ background: story.style.colors.background }" :class="story.name">

    <div class="wrapper">

      <div class="button-wrapper">
        <div :class="currentGraph === question ? 'button active' : 'button'" v-for="(title, question) in questionTitle" :key="title" @click="changeGraph(question)">

          <div :class="`image ${title}`"></div>

          {{title}}

        </div>
      </div>

      <hr :style="{ background: story.style.colors.hr }">

      <div v-if="currentGraph === 'time'" class="time-wrapper">

        <div class="time">

          <div class="clock-wrapper">

            <div class="clock" v-for="clock in getClockNumber(startForm[currentGraph])" :key="clock">

              <img :src="require(`@/assets/img/${story.style.clock}`)" alt="clock" class="clock-image">

              <div v-if="clock !== 1" :style="`background: conic-gradient(${story.style.colors.time} 0deg ${360 * clock}deg, transparent ${360 * clock}deg 360deg); width:75px; height:75px;border-radius: 100%; z-index: 1;`"></div>
              <div v-else :style="`background: ${story.style.colors.time}; width:75px; height:75px;border-radius: 100%; z-index: 1;`"></div>

            </div>

          </div>

          <div class="perso-wrapper">

            <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)">

            <p :style="{ color: story.style.colors.textTime }">{{startForm[currentGraph]}} min</p>

          </div>

        </div>

        <div class="time">

          <div class="clock-wrapper">

            <div class="clock" v-for="clock in getClockNumber(story[currentGraph])" :key="clock">

              <img :src="require(`@/assets/img/${story.style.clock}`)" alt="clock" class="clock-image">

              <div v-if="clock !== 1" :style="`background: conic-gradient(${story.style.colors.time} 0deg ${360 * clock}deg, transparent ${360 * clock}deg 360deg); width:75px; height:75px;border-radius: 100%; z-index: 1;`"></div>
              <div v-else :style="`background: ${story.style.colors.time}; width:75px; height:75px;border-radius: 100%; z-index: 1;`"></div>

            </div>

          </div>

          <div class="perso-wrapper">

            <img :src="require(`@/assets/img/${story.style.iconChildren}`)">

            <p :style="{ color: story.style.colors.textTime }">{{story[currentGraph]}}</p>

          </div>

        </div>

      </div>

      <div v-if="currentGraph === 'distance'" class="distance-wrapper">

        <div class="distance">
          <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)" alt="personnage" class="personnage">
          <p class="km" :style="{ color: story.style.colors.km }">{{startForm[currentGraph]}} km</p>

        </div>

        <div class="distance">
          <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="personnage" class="personnage">
          <p class="km" :style="{ color: story.style.colors.km }">{{story[currentGraph]}}</p>
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
      const timeInMinute = this.getTimeInMinute(time)
      const timeInHours = timeInMinute / 60
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
