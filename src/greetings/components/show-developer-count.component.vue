<script>

export default {
  name: 'show-developer-count',
  props: {
    developerCount: {
      type: Number,
      required: true,
    }
  }
}
</script>

<template>
  <div>
    <p>Developers registered: {{ developerCount }}</p>
  </div>
</template>

<style scoped>

</style>