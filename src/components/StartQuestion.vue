<template>
  <section id="startQuestion">
    <div v-for="input in inputs" :key="input.title" :class="input.model">

      <h3 class="title">{{ input.title }}</h3>

      <div class="container">
        <div class="item" v-for="option in input.options" :key="option.value" @click="updateForm(option.value, input.model)">

            <img v-if="input.model === 'personnage'" :src="require(`@/assets/img/basicPerso/${option.display}`)">

          <div class="wrapper" v-else-if="input.model === 'transport'"></div>

            <div class="wrapper" v-else>

              <div class="image"></div>

              <p>{{ option.display }}</p>

            </div>

        </div>
      </div>

    </div>

    <button @click="saveForm" class="saveButton">Valider</button>

  </section>
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
        time: null
      }
    }
  },
  methods: {
    saveForm() {
      this.$emit('startForm', this.models)
    },
    updateForm(value, model) {
      this.models[model] = value
    }
  }
}
</script>

<style scoped>

</style>
