<template lang="html">

  <div id="select-div">
    <select @change="characterSelected">
      <option selected disabled>-select character-</option>
      <option v-for="(character, index) in characters" :value="index">{{ character.name }}</option>
    </select>
  </div>

</template>

<script>
import { eventBus } from '@/main.js'

export default {
  name: 'character-select',
  props: ['characters'],

  methods: {
    characterSelected(e) {
      const selectedIndex = e.target.value;
      eventBus.$emit('character-selected', selectedIndex);
    }
  }
}
</script>

<style>
  #select-div {
    display: flex;
    justify-content: center;
  }
</style>
