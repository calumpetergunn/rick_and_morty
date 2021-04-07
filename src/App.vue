<template>
  <div id="app">
    <p>Hi there!</p>
    
    <character-list :characters="characters"/>
    <character-details v-if="selectedCharacter" :character="selectedCharacter" />
  </div>
</template>

<script>
import {eventBus} from './main.js'
import CharacterList from './components/CharacterList.vue';
import CharacterDetails from './components/CharacterDetails.vue';

export default {
  name: 'App',
  data() {
    return {
      characters: [],
      selectedCharacter: null
    }
  },
  components: { 
    "character-list": CharacterList,
    "character-details": CharacterDetails,
  
  },
  mounted() {
    fetch('https://rickandmortyapi.com/api/character/')
    .then(result => result.json())
    .then(characters => this.characters = characters.results)

  eventBus.$on('character-selected', (character) => {
    this.selectedCharacter = character;
  })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
