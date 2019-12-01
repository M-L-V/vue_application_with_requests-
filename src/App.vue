<template lang="html">
  <div>

    <h1> Studio Ghibli characters API </h1>
    <div>
      <characters-list :characters='characters'></characters-list>
      <selected-character :character='selectedCharacter'></selected-character>

    </div>
    

  </div>

</template>





<script>

import CharactersList from './components/CharactersList.vue'


export default {
  data(){
    return {
      characters: [],
      selectedCharacter: null    }
  },
  components: {
    "characters-list": CharactersList,
    // "character-detail": CharacterDetail
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/people')
    .then(res => res.json())
    .then(characters => this.characters = characters)


  }
}














</script>









<style lang="css" scoped>
</style>
