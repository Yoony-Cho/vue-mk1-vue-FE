<template>
    <div class="black-bg" v-if="modalOpen === true">
    <div class="white-bg">
      <h4>{{ citiesData[clickNum].name }}</h4>
      <img :src="citiesData[clickNum].image">
      <p>Area : {{ citiesData[clickNum].area }}</p>
      <p>Population : {{ citiesData[clickNum].population }}</p>
      <p>Province : {{ citiesData[clickNum].province }}</p>

      <!-- props is read only -->
      <!-- <button @click="modalOpen=false">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
    name : 'DetailModal',
    props : {
      citiesData : Array,
      clickNum : Number,
      modalOpen : Boolean,
    }
}
</script>

<style>
    .black-bg {
    width: 100%; 
    height:100%;
    background: rgba(0,0,0,0.5);
    position: fixed; 
    padding: 20px;
    justify-content: center;
    text-align: center;
    }
    .white-bg {
    width: 100%; 
    max-width: 500px;
    background: white;
    border-radius: 8px;
    padding: 40px;
    margin-left: auto;
    margin-right: auto;
    }

    .white-bg img {
    width: 100%; 
    height: 200px;
    border-radius: 8px;

    }
</style>