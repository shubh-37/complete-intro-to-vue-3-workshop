<script>
export default {
  data() {
    return {
      charactersList: [
        { name: 'Jon Snow', fav: false, house: 'Targeryen' },
        { name: 'Arya Star', fav: false, house: 'Stark' },
        { name: 'Cersei', fav: false, house: 'Lanister' },
        { name: 'Danerys', fav: false, house: 'Targeryen' }
      ],
      favoriteCharactersList: [],
      characterName: {
        name: ''
      }
    }
  },
  methods: {
    addtoFav(character) {
      this.favoriteCharactersList.push(character)
    },
    addANewCharacter() {
      this.charactersList.push(this.characterName)
      this.characterName = { name: '' }
    }
  },
  computed: {
    getStats() {
      const stats = this.charactersList.reduce(
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
  <div id="app">
    <h4>Statistics</h4>
    <ul>
      <li v-for="(key, st) in getStats" :key="`${key}-${st}`">{{ st }} : {{ key }}</li>
    </ul>
    <ul>
      <li v-for="(character, index) in charactersList" :key="`${character}-${index}`">
        {{ character.name }}
        <button @click="addtoFav(character)">Add to fav</button>
      </li>
    </ul>
    <ul v-if="favoriteCharactersList.length > 0">
      <li v-for="(character, index) in favoriteCharactersList" :key="`${character}-${index}`">
        {{ character.name }}
      </li>
    </ul>
    <p v-else>There are no favorite characters yet</p>
    <p>Add a new character</p>
    <input type="text" v-model="characterName.name" v-on:keyup.enter="addANewCharacter" />
  </div>
</template>
