<template>

  <div class="black-bg" v-if="모달창 == true">
   <div class="white-bg">
     <h4>상세페이지</h4>
     <p>상세페이지 내용</p>
     <button @click="모달창 = false">닫기</button>
   </div>
  </div>

  <div class="menu">
    <a v-for="main in menus" :key="main">{{ main }}</a>
  </div>
  
  <div class="products">
    <div v-for="(room, index) in 원룸들" :key="index">
      <img :src="room.image" class="room-img">
      <h4 @click="모달창 = true">{{ room.title }}</h4>
      <p>{{ room.price }}원</p>
      <button @click="신고수[index]++">허위매물신고</button> <span>신고수 : {{ 신고수[index] }}</span>
    </div>
  </div>
</template>

<script>

import data from './assets/data.js';

export default {
  name: 'App',
  data(){
    return {
      원룸들 : data,
      모달창 : true,
      신고수 : [0,0,0,0,0,0],
      menus : ['Home', 'Shop', 'About'],
     // products : ['평거동원룸', '하대동원룸', '칠암동원룸', '판문원룸', '신안원룸', '이현원룸' ],
    }
  },
  methods : {
    increase(){
      this.신고수 += 1;
    }
  },
  components: {
    
  }
}
</script>

<style>
body {
  margin : 0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background : rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
}
</style>

