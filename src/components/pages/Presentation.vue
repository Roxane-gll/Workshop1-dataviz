<template>
  <div>
    <section id="presentation" :class="story.name">

      <div class="presentation-wrapper">

        <img :src="require(`@/assets/img/${story.style.backgroundChooseChildren}`)" alt="background Children" class="backgroundPresentation">

        <img :src="require(`@/assets/img/${story.style.iconChildren}`)" alt="icon Children" class="icon">

        <div class="info-presentation">

          <h3 class="name" :style="{ color: story.style.colors.presentation }">{{ story.name }}</h3>

          <h5 class="age" :style="{ color: story.style.colors.presentation }">{{ story.age }} ans</h5>

        </div>


      </div>

      <div class="content-wrapper" :style="{ background: story.style.colors.background }">

        <div class="top-part">

          <h6 class="hey" :style="{ color: story.style.colors.hey }">Salut !</h6>

          <p class="p1" v-html="story.content.presentation.p1"></p>

          <p class="p2" v-html="story.content.presentation.p2"></p>

        </div>

        <div class="bottom-part">

          <p class="p1" v-html="story.content.presentation.p3"></p>

        </div>

        <img :src="require(`@/assets/img/${story.style.country}`)" alt="Country" class="country">

      </div>

    </section>

    <audio :src="require(`@/assets/sounds/${getAudio}`)" autoplay></audio>

  </div>

</template>

<script>
export default {
  name: 'Presentation',
  props: {
    story:{
      type: Object
    }
  },
  computed: {
    getAudio() {
      return this.story.sounds.presentation
    }
  }
}
</script>

<style scoped>
</style>
