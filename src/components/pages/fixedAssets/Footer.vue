<template>
  <div id="app">
    <footer>

      <div v-if="currentPage > 1" class="arrow prev" :style="{ background: story.style.colors.arrow, color: story.style.colors.arrow }"  @click="changePage(-1)">
        <img src="@/assets/img/arrow.svg" alt="arrow">
      </div>

      <div v-if="currentPage < nbPages" class="arrow next" :style="{ background: story.style.colors.arrow, color: story.style.colors.arrow }" @click="changePage(1)">
        <img src="@/assets/img/arrow.svg" alt="arrow">
      </div>

    </footer>
  </div>
</template>

<script>

export default {
  name: 'Footer',
  props: {
    story: {
      type:Object
    },
    currentPage: {
      type:Number
    },
    nbPages: {
      type: Number
    }
  },
  methods: {
    changePage(newPageId) {
      this.$emit('newPage', newPageId)
    }
  }
}
</script>

<style scoped>

</style>
