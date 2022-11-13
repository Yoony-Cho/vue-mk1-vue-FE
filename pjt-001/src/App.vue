<template>
  <div class="black-bg" v-if="modalOpen" @click="modalOpen=false">
    <div class="white-bg">
      <h4>{{ citiesData[clickNum].name }}</h4>
      <img :src="citiesData[clickNum].image">
      <p>Area : {{ citiesData[clickNum].area }}</p>
      <p>Population : {{ citiesData[clickNum].population }}</p>
      <p>Province : {{ citiesData[clickNum].province }}</p>
      <button @click="modalOpen=false">닫기</button>
    </div>
  </div>

  <div>
    <div class="nav-bar">
      <a v-for="menu in menus" :key="menu"> {{menu}} </a>
    </div>
    <div class="main-container">
      <div class="item-container" v-for="(city, idx) in citiesData" :key="idx">
        <img :src="city.image" class="imgs" @click="modalOpen=true; clickNum = idx">
        <h4>{{ city.name }}</h4>
        <p>Province: {{ city.province }}</p>
        <div class="like-btn">
          <button @click="increase(idx)">like👍</button>
          <p>{{ city.like }}</p>
        </div>
      </div>
    </div>
</div>
</template>

<script>

import dataSet from './assets/data'

export default { 
  name: 'App',
  data(){
    return{
      clickNum : 0,
      citiesData : dataSet,
      cities : [
        {name : "Vancouver", Population : "662,248" , like : 0, pic : "https://p4.wallpaperbetter.com/wallpaper/193/562/539/the-city-canada-vancouver-wallpaper-preview.jpg"},
        {name : "Toronto", Population : "2,794,356", like : 0, pic : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQpnJ9Cl_9yyfyl1fU-6GuXBooa-c00Z4nWMfo-dpJG6Ac0YbLAOaNas6R7cfjKLZVOnjg&usqp=CAU'},
        {name : "Montreal", Population : "1,762,949", like : 0, pic : 'http://www.uhaknet.co.kr/data/cheditor4/1505/dsmSk4ijDesgBeMSV.jpg'},
        {name : "Ottawa", Population : "1,017,449", like : 0, pic : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQM_2xG7DjhRjLvtE_qwVsCG8VFQF90PpaZfS3w1JjqrIzh8ftFf7_QroXgmgJ13HfJcIw&usqp=CAU'},
        {name : "Calgary", Population : "1,306,784", like : 0, pic : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQSd55KK3T_YGgaaLtYExEP5Bz-CeIxvh6CT2vXcQRq1e1KgqwrbfYiaX89rdCbG-vOkAQ&usqp=CAU'},
        {name : "Edmonton", Population : "1,010,899	", like : 0, pic : 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTtbXASqSUhyndAkNz1-t3tFDNDCYsRfWjI9TnaDC56Ujd4Pf7ykFgH2Azo4RU1U5NQCH8&usqp=CAU'},
      ],
      menus : [
        "Home",
        "Product",
        "About"
      ],
      modalOpen : false,
    }
  },
  methods : {
    increase(idx){
      this.cities[idx].like += 1
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
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

.nav-bar {
  background-color: #ff000a;
  padding: 20px;
  border-radius: 6px;
}

.nav-bar a {
  color: white;
  padding: 16px;
}

.main-container {
  gap: 20px !important;
}

.item-container {
  /* border: 1px solid #ff999d; */
  margin-bottom: 20px;
  margin-top: 20px;
}

.item-container .imgs {
  /* border: 1px solid #ff999d; */
  width: 300px;
  height: 150px;
  margin-top: 20px;
  border-radius: 8px;
  overflow: hidden;
}

.item-container .like-btn{
  display: flex;
  justify-content: center;
  align-items: center;
}

.item-container .like-btn button{
  height: 34px;
  align-items: center;
}
</style>
