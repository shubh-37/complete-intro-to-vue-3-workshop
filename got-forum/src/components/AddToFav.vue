<script>
export default {
  props: {
    favorites: {
      type: Array,
      required: true
    }
  }
}
</script>
<template>
  <ul v-if="favorites.length > 0">
    <li v-for="(character, index) in favorites" :key="`${character}-${index}`">
      {{ character.name }}
    </li>
  </ul>
  <p v-else>There are no favorite characters yet</p>
</template>
