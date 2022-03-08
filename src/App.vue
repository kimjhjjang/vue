<template>
  <div @click="modal=false" class="black-bg" v-if="modal == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>이런저런 내용</p>
    </div>
  </div>

  <div class="menu">
    <a v-for="(header) in menu" :key="header">{{header}}</a>
  </div>
  <p>전체 신고수 : {{countSum}} </p>
  <div v-for="(item,i) in items"  v-bind:key="item">
    <img class="room-img" :src="item.img" alt="loading..."/>
    <h4 @click="modal=true">{{item.product}}</h4>
    <p>{{item.price}} 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수 : {{police[i]}}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      modal : false,
      items : [
        {
          product : '역삼동원룸',
          price: 160,
          img : require("./assets/room0.jpg")
        },
        {
          product : '천호동원룸',
          price: 60,
          img : require("./assets/room1.jpg")
        },
        {
          product : '마포구원룸',
          price: 110,
          img : require("./assets/room2.jpg")
        }
      ],
      menu: ['홈','상품','어바웃'],
      police: [0,0,0],
      countSum : 0,
    }
  },
  methods: {
    increase(i){
      this.police[i] += 1;
      this.countSum = this.police.reduce( (prev, curr) => 
        prev + curr
      );
    }
  },
  components : {

  }
}
</script>

<style>
body{
  margin:0;
}

div {
  box-sizing: border-box;
}

.black-bg{
  width: 100%; height:100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed;
  padding:20px;
}

.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding:20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin:15px 0px;
}
</style>
