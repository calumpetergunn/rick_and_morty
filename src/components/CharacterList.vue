<template>
  <section>
      <ul>
          <character-select v-for="(character, index) in characters" :character="character" :key="index"/>
      </ul>
  </section>
</template>

<script>
import CharacterSelect from './CharacterSelect.vue';

export default {
    name: 'character-list',
    props: ['characters'],
    components : {
        "character-select": CharacterSelect
    }
}
</script>

<style scoped>

</style>