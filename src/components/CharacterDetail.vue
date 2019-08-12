<template lang="html">

  <div id="detail-div">

    <div v-if="character !==null" class="info-frame">
      <ul>
        <li><span class="name-detail">NAME: </span>{{ character.name }}</li>
        <li><span class="info-detail">STATUS: </span>{{ character.status }}</li>
        <li><span class="info-detail">SPECIES: </span>{{ character.species }}</li>
        <li><span class="info-detail">GENDER: </span>{{ character.gender }}</li>
        <li><span class="info-detail">ORIGIN: </span>{{ character.origin.name }}</li>
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
    border-width: 12px;
    border-color: #480056;
    background-color: hotpink;
    display: flex;
    justify-content: left;
    margin-left: 30%;
    margin-right: 30%;
    margin-bottom: 20px;
    box-shadow: 1px 10px 20px #480056;
   }

  .image-frame {
    margin-left: 30%;
    margin-right: 30%;
    margin-bottom: 100px;
    padding: 3%;
    border-style: solid;
    border-width: 14px;
    border-color: #73BF26;
    background-color: #42B8CD;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    box-shadow: 1px 10px 20px #480056;
  }

  .name-detail {
    font-size: 24px;
    font-family: arial;
    font-weight: bold;
    color: #480056;
  }

  .info-detail {
    font-size: 18px;
    font-family: arial;
    font-weight: bold;
    color: #480056;
  }

  li {
    list-style: none;
    font-family: arial;
  }



</style>
