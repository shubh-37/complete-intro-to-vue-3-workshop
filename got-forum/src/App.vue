<script>
import AddToFavVue from './components/AddToFav.vue'
import StatisticsForGotVue from './components/StatisticsForGot.vue'
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
    addANewCharacter() {
      this.charactersList.push(this.characterName)
      this.characterName = { name: '' }
    },
    addtoFav(character) {
      this.favoriteCharactersList.push(character)
    }
  },
  components: {
    AddToFavVue,
    StatisticsForGotVue
  }
}
</script>

<template>
  <div id="app">
    <statistics-for-got-vue :characters="charactersList" />
    <ul>
      <li v-for="(character, index) in charactersList" :key="`${character}-${index}`">
        {{ character.name }}
        <button @click="addtoFav(character)">Add to fav</button>
      </li>
    </ul>
    <add-to-fav-vue :favorites="favoriteCharactersList" />
    <p>Add a new character</p>
    <input type="text" v-model="characterName.name" v-on:keyup.enter="addANewCharacter" />
  </div>
</template>
