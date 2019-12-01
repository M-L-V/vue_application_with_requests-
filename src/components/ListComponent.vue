<template lang="html">
<li v-on:click="handleClick">{{character.name}}</li>
</template>




<script>
export default {
  name: 'list-component',
  props: ['character'],
  methods: {
    handleClick(){
      eventBus.$emit('character-selected', this.character)
    }
  }
}
</script>





<style lang="css" scoped>
</style>
