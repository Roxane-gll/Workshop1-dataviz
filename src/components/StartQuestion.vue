<template>
  <div>
      <form>
          <div v-for="input in inputs" :key="input.title">
              <label :for="input.title">{{ input.title }}</label>
              <div style="display:flex;">
                <div v-for="option in input.options" :key="option.value">
                  <div @click="updateForm(option.value, input.model)">

                    <img v-if="input.model === 'personnage'" :src="require(`@/assets/img/${option.display}`)">
                    
                    <div v-else>{{option.display}}</div>

                  </div>
                </div>
              </div>
          </div>
          <button @click="saveForm">Save</button>
      </form>
  </div>
</template>

<script>
import inputs from '../assets/startForm.json'

export default {
  name: 'StartForm',
  props: {
      story: {
          type:Number
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
