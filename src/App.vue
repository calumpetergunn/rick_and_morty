<template>
  <div id="app">
    <p>Hi there!</p>
    
    <character-list :characters="characters"/>
  </div>
</template>

<script>
import CharacterList from './components/CharacterList.vue';

export default {
  name: 'App',
  data() {
    return {
      characters: []
    }
  },
  components: { 
    "character-list": CharacterList
  
  },
  mounted() {
    fetch('https://rickandmortyapi.com/api/character/')
    .then(result => result.json())
    .then(characters => this.characters = characters.results)
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
