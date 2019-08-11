<template lang="html">

  <div id="detail-div">

    <div class="info-frame">
      <ul v-if="character !==null">
        <li><span class="name-detail">Character: </span>{{ character.name }}</li>
        <li><span class="info-detail">Status: </span>{{ character.status }}</li>
        <li><span class="info-detail">Species: </span>{{ character.species }}</li>
        <li><span class="info-detail">Gender: </span>{{ character.gender }}</li>
        <li><span class="info-detail">Origin: </span>{{ character.origin.name }}</li>
      </ul>
    </div>

    <div v-if="character !==null" class="image-frame">
      <img :src="character.image" alt="">
    </div>

  </div>



</template>

<script>
export default {
  name: 'character-detail',
  props: ['character']
}
</script>

<style lang="css" scoped>
  #detail-div {
    margin-top: 60px;
    display: flex;
    justify-content: center;
    flex-direction: column;
  }

  .char-name {
    font-size: 20px;
    font-family: arial;
  }

  .info-frame {
    border-style: solid;
    display: flex;
    justify-content: center;
   }

  .image-frame {
    border-style: solid;
    border-color: blue;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }

  .name-detail {
    font-size: 20px;
  }
</style>
