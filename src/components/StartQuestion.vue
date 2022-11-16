<template>
  <div>
      <form>
          <div v-for="input in inputs" :key="input.title">
              <label :for="input.title">{{ input.title }}</label>
              <input :name="input.title" v-model="models[input.model]">
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
          q1: null,
          q2: null,
          q3: null
      }
    }
  },
  methods: {
    saveForm() {
        this.$emit('startForm', this.models)
    }
  }
}
</script>

<style scoped>

</style>
