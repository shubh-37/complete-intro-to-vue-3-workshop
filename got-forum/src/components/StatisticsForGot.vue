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
    },
    percentageOfDomination() {
      console.log(Object.keys(this.getStats))
      const aggregatedVal = Object.keys(this.getStats).reduce(
        (acc, item) =>
          acc[item]
            ? { ...acc }
            : { ...acc, [item]: ((this.getStats[item] / this.characters.length) * 100).toFixed() },
        {}
      )
      return aggregatedVal
    }
  }
}
</script>
<template>
  <div>
    <h4>Domination Stats</h4>
    <ul>
      <li v-for="(key, st) in percentageOfDomination" :key="`${key}-${st}`">
        {{ st }} : {{ key }}%
      </li>
    </ul>
    <h4>Count Stats</h4>
    <ul>
      <li v-for="(key, st) in getStats" :key="`${key}-${st}`">{{ st }} : {{ key }}</li>
    </ul>
  </div>
</template>
