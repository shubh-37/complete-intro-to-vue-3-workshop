<script>
import StatisticsForGotVue from './components/StatisticsForGot.vue'
import CharacterCard from './components/CharacterCard.vue'
import BaseLayout from './components/BaseLayout.vue'
export default {
  data() {
    return {
      charactersList: [
        { name: 'Jon Snow', fav: false, house: 'Targeryen' },
        { name: 'Arya Star', fav: false, house: 'Stark' },
        { name: 'Cersei', fav: false, house: 'Lanister' },
        { name: 'Danerys', fav: false, house: 'Targeryen' }
      ],
      favorites: [],
      characterName: {
        name: '',
        house: 'HighTower'
      }
    }
  },
  methods: {
    addANewCharacter() {
      this.charactersList.push(this.characterName)
      this.characterName = { name: '', house: 'HighTower' }
    },
    addtoFav(payload) {
      this.favorites.push(payload)
    }
  },
  components: {
    CharacterCard,
    StatisticsForGotVue,
    BaseLayout
  }
}
</script>

<template>
  <div id="app">
    <base-layout>
      <template #one>
        <p>Add a new character</p>
        <input type="text" v-model="characterName.name" v-on:keyup.enter="addANewCharacter" />
      </template>
    </base-layout>
    <statistics-for-got-vue :characters="charactersList" />
    <ul>
      <li v-for="(character, index) in charactersList" :key="`${character}-${index}`">
        <character-card :character="character" @addToFav="addtoFav" />
      </li>
    </ul>
    <ul v-if="favorites.length > 0">
      <h4>Favorites list</h4>
      <li v-for="(character, index) in favorites" :key="`${character}-${index}`">
        {{ character.name }}
      </li>
    </ul>
    <p v-else>There are no favorite characters yet</p>
  </div>
</template>
