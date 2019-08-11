<template>
  <div>
    <div id="header-div">
      <h1>Rick and Morty - characters library</h1>

    </div>
    <div class="content-div">
      <character-select :characters="characters" />
      <character-detail :character="selectedCharacter" />
    </div>
  </div>
</template>

<script>
import { eventBus } from '@/main.js'
import CharacterDetail from './components/CharacterDetail.vue'
import CharacterSelect from './components/CharacterSelect.vue'


export default {

  data(){
    return {
      characters: [],
      selectedCharacter: null
    }
  },

  mounted(){
    eventBus.$on('character-selected', (selectedIndex) => {
      this.selectedCharacter = this.characters[selectedIndex];
    });


    let pg1 = fetch('https://rickandmortyapi.com/api/character?page=')
              .then(res => res.json())
    let pg2 = fetch('https://rickandmortyapi.com/api/character?page=2')
              .then(res => res.json())

    Promise.all([pg1, pg2])
    .then(pages => pages.forEach(page => this.characters.push(page.results)))





    // fetch('https://rickandmortyapi.com/api/character?page=')
    // .then(res => res.json())
    // .then(characters => this.characters = characters.results)

  },











  components: {
    "character-select": CharacterSelect,
    "character-detail": CharacterDetail
  }

}

</script>

<style>

#header-div {
  margin-top: 50px;
  margin-bottom: 50px;
}

h1 {
  font-family: arial;
  text-align: center;
}
</style>
