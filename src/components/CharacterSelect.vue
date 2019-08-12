<template lang="html">

  <div id="select-div">
    <select @change="characterSelected" class="selector">
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

  .selector {
    padding-left: 50px;
    font-size: 16px;
    font-family: sans-serif;
    font-weight: 700;
    border-style: solid;
    border-width: 6px;
    border-color: #73BF26;
    background-color: #480056;
    color: #73BF26;
    box-shadow: 1px 10px 20px #480056;
  }
</style>
