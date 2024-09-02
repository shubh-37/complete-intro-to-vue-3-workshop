<script>
export default {
  props: {
    character: {
      type: Object,
      required: true
    }
  },
  methods: {
    addToFav() {
      this.$emit('addToFav', this.character)
    }
  }
}
</script>
<template>
  <div>
    <h4>{{ character.name }}</h4>
    <button @click="addToFav">Add to fav</button>
  </div>
</template>
