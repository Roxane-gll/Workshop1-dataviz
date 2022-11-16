<template>
  <div class="hello">
    {{story.content.p1}}
  </div>
</template>

<script>
export default {
  name: 'Graph',
  props: {
    story:{
      type: Object
    }
  }
  
}
</script>
