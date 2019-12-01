<template lang="html">
  <div>
    <h1> Studio Ghibli characters API </h1>
    <div>
      <characters-list :characters='characters'></characters-list>
      <character-detail :character='selectedCharacter'></character-detail>
    </div>
  </div>

</template>


<script>

import { eventBus } from './main.js'
import CharactersList from './components/CharactersList.vue'
import CharacterDetail from './components/CharacterDetail.vue'


export default {
  data(){
    return {
      characters: [],
      selectedCharacter: null    }
  },
  components: {
    "characters-list": CharactersList,
    "character-detail": CharacterDetail
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/people')
    .then(res => res.json())
    .then(characters => this.characters = characters)

    eventBus.$on('character-selected', (character) => {
      this.selectedCharacter = character
    })
  }
}

</script>





<style lang="css" scoped>
</style>
