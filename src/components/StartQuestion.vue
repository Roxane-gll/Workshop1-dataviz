<template>

  <div id="app">
    <header>
      <div @click="sendIntro" class="goHome-wrapper" style="background: transparent">
        <img src="../assets/img/restart.svg" alt="home button">
      </div>
    </header>

    <section id="startQuestion">
      <div v-for="input in inputs" :key="input.title" :class="input.model">

        <h3 class="title">{{ input.title }}</h3>

        <div class="container">
          <div :class="models[input.model] === option.value ? 'item active': 'item'" v-for="option in input.options" :key="option.value" @click="updateForm(option.value, input.model)">

            <img v-if="input.model === 'personnage'" :src="require(`@/assets/img/basicPerso/${option.display}`)" :style="models[input.model] === option.value || models[input.model] === null ? '' : 'transition: all 0.35s ease-in-out;'">

            <div class="wrapper" v-else-if="input.model === 'transport'" @click="updateForm(option.value, input.model)"></div>

            <div :class="models[input.model] === option.value ? 'wrapper active': 'wrapper'" v-else @click="updateForm(option.value, input.model)">
              <div class="image"></div>

              <p>{{ option.display }}</p>
            </div>
          </div>
        </div>

      </div>

      <button @click="saveForm" class="saveButton">Valider</button>

    </section>

  </div>

</template>

<script>
import inputs from '../assets/startForm.json'

export default {
  name: 'StartForm',
  props: {
    story: {
      type: Number
    }
  },
  data() {
    return {
      inputs,
      models: {
        personnage: null,
        transport: null,
        time: null,
        distance: null
      }
    }
  },
  methods: {
    saveForm() {
      if(!this.models.personnage || !this.models.transport|| !this.models.time) {
        return
      }
      this.getDistance()
      this.$emit('startForm', this.models)
    },
    updateForm(value, model) {
      this.models[model] = value
    },
    sendIntro() {
      this.$emit('intro')
    },
    getDistance() {
      if (this.models.time === "5") {
        this.models.distance = "1"
      } if (this.models.time === "15") {
        if (["walk", "bike"].includes(this.models.transport)) {
          this.models.distance = "1"
        } else {
          this.models.distance = "3"
        }
      } if (this.models.time === "30") {
        if (["walk", "bike"].includes(this.models.transport)) {
          this.models.distance = "2"
        } else {
          this.models.distance = "4"
        }
      } if (this.models.time === "60") {
        if (["walk", "bike"].includes(this.models.transport)) {
          this.models.distance = "4"
        } else {
          this.models.distance = "6"
        }
      }
    }
  }
}
</script>

<style scoped>

</style>
