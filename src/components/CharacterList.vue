<template>
  <section>
      <select @change="handleSelect($event)">
          <option selected disabled value="">Select a character:</option>
          <character-select v-for="(character, index) in characters" :character="character" :key="index"/>
      </select>
  </section>
</template>

<script>
import {eventBus} from '../main.js'

import CharacterSelect from './CharacterSelect.vue';

export default {
    name: 'character-list',
    props: ['characters'],
    components : {
        "character-select": CharacterSelect
    },
    methods: {
        handleSelect: function(event) {
            console.log(event.target.value)
            const selectedName = event.target.value;
            eventBus.$emit('character-selected', this.characters.find(character => character.name === selectedName))
            console.log(this.characters.find(character => character.name === selectedName))



        }
    }
}
</script>

<style scoped>

</style>