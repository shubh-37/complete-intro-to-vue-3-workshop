<script>
export default {
  props: {
    characters: {
      type: Array,
      required: true
    }
  },
  computed: {
    getStats() {
      const stats = this.characters.reduce(
        (acc, item) =>
          acc[item.house]
            ? { ...acc, [item.house]: acc[item.house] + 1 }
            : { ...acc, [item.house]: 1 },
        {}
      )
      return stats
    }
  }
}
</script>
<template>
  <div>
    <h4>Statistics</h4>
    <ul>
      <li v-for="(key, st) in getStats" :key="`${key}-${st}`">{{ st }} : {{ key }}</li>
    </ul>
  </div>
</template>
