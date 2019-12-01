<template lang="html">

<div v-if='character'>
  <h1> {{character.name}} </h1>
  <p> Age: {{character.age}} </p>
  <p> Gender: {{character.gender}} </p>
  <p> Hair Colour: {{character.hair_color}} </p>
</div>

</template>


<script>
export default {
  name: 'character-detail',
  props: ['character']
}

</script>





<style lang="css" scoped>
</style>
