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
          <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="personnage" class="personnage">

          <lottie-player class="lottieOlivier" v-if="story.name === 'olivier'" autoplay mode="normal" src="https://assets9.lottiefiles.com/packages/lf20_TiDTPBoL6W.json"></lottie-player>
          <lottie-player class="lottieDevi" v-if="story.name === 'devi'" autoplay mode="normal" src="https://assets6.lottiefiles.com/packages/lf20_zydCtDYIVH.json"></lottie-player>
          <lottie-player class="lottieFrigg" v-if="story.name === 'frigg'" autoplay mode="normal" src="https://assets1.lottiefiles.com/packages/lf20_olU1R45lIZ.json"></lottie-player>
          <lottie-player class="lottieCarlos" v-if="story.name === 'carlos'" autoplay mode="normal" src="https://assets6.lottiefiles.com/packages/lf20_JPb7TebJkI.json"></lottie-player>

          <p class="km" :style="{ color: story.style.colors.km }">{{story[currentGraph]}}</p>

        </div>

        <div class="distance">
          <img :src="require(`@/assets/img/basicPerso/${startForm.personnage}`)" alt="personnage" class="personnage">

          <lottie-player class="lottie" v-if="story.name === 'olivier'" autoplay mode="normal" src="https://assets10.lottiefiles.com/packages/lf20_x8sj9dGuxw.json"></lottie-player>
          <lottie-player class="lottie" v-if="story.name === 'devi'" autoplay mode="normal" src="https://assets2.lottiefiles.com/packages/lf20_16jiNKbN1h.json"></lottie-player>
          <lottie-player class="lottie" v-if="story.name === 'frigg'" autoplay mode="normal" src="https://assets3.lottiefiles.com/packages/lf20_37uqNsAka2.json"></lottie-player>
          <lottie-player class="lottie" v-if="story.name === 'carlos' " autoplay mode="normal" src="https://assets3.lottiefiles.com/packages/lf20_mD1e5k2g5n.json"></lottie-player>


          <p class="km" :style="{ color: story.style.colors.km }">{{startForm[currentGraph]}} km</p>

        </div>

      </div>

    </div>

  </section>

</template>

<script>

require("@lottiefiles/lottie-player");

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
