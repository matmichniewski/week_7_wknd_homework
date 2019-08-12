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
    let pg3 = fetch('https://rickandmortyapi.com/api/character?page=3')
              .then(res => res.json())
    let pg4 = fetch('https://rickandmortyapi.com/api/character?page=4')
              .then(res => res.json())
    let pg5 = fetch('https://rickandmortyapi.com/api/character?page=5')
              .then(res => res.json())
    let pg6 = fetch('https://rickandmortyapi.com/api/character?page=6')
              .then(res => res.json())

    Promise.all([pg1, pg2, pg3, pg4, pg5, pg6].flat())
    .then(pages => pages.forEach(page => this.characters.push(page.results)))
    .then(a => console.log(this.characters.flat()))




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
  font-size: 50px;
  font-family: arial;
  text-align: center;
  color: #42B8CD;
  stroke: #73BF26;
  shadow: 1px 10px 20px #480056;
}
</style>
