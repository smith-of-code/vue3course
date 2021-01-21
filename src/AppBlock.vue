<template>
  <div class="card">
    <slot name="header"></slot>
    <slot name="content">no text</slot>
  </div>

</template>

<script>
export default {
  name: 'AppBlock'
}
</script>

<style scoped>

</style>
