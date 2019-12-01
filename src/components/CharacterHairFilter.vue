<template lang="html">
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="search for character..." v-on:keyup="searchForCharacter">
    <select v-on:change="handleSelect" v-model="selectedCharacter">
      <option disabled value="">Select a character by hair colour...</option>
      <option v-for="character in characters" :value="character">{{character.hair_color}}</option>
    </select>
  </form>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: "character-hair-filter",
  data(){
    return {
      "search": "",
      "selectedCharacter": {},
    }
  },
  props: ["characters"],
  methods: {
    searchForCharacter(){
      let foundCountry = this.countries.find((country) => { //.find will return the first thing it finds
        return country.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedCountry = foundCountry //cannot be written other way round

      eventBus.$emit('character-selected', this.selectedCharacter)
    },
    handleSelect(){
      this.search = ""
      eventBus.$emit('character-selected', this.selectedCharacter)
    }
  }
}
</script>

<style lang="css" scoped>
form{
  text-align: center;
  margin: 40px 0;
}

select, input[type="text"]{
  font-size: 18px;
}

select {
  margin-left: 20px;
}
</style>
