<template>
  <div class="hello">
    {{story.name}}
  </div>
</template>

<script>
export default {
  name: 'Stories',
  props: {
    story:{
      type: Object
    }
  }
  
}
</script>

<style scoped>
</style>
