<template>
  <div class="black-bg" v-if="openModal == true">
    <div class="white-bg"> 
      <h4>{{원룸들[clickCheck].title}}</h4>
      <p>{{원룸들[clickCheck].content}}</p>
      <button @click="openModal=false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="menu in menus" :key="menu"> {{ menu }} </a>
    
  </div>
 <div v-for="(i, p) in 원룸들" :key="p">
    <!-- <p>{{p}}</p> -->
    <img :src="원룸들[p].image" class="room-img">
    <h4 @click="openModal = true; clickCheck=p">{{원룸들[p].title}}</h4>
    <p>{{원룸들[p].price}}원</p>
 </div>

 <br>
  <button v-on:click="신고수[0]++">허위매물신고</button> <span>신고 수 : {{신고수}}</span>
  <button v-on:mouseover="신고수[1]++">허위매물신고</button> <span>신고 수 : {{신고수}}</span>
  <button v-on:mouseover="increase()">허위매물신고</button> <span>신고 수 : {{신고수}}</span>  <!--vue 함수 만드는 방법-->
  
</template>

<script>
import data from './assets/data'

export default {
  name: 'App',
  data() {
    return {
      clickCheck : 0,
      원룸들 :  data,
      openModal : false, //true은 열림, false은 닫힘
       신고수 : [0,0,0],
      products : ['역삼동원룸' , '마포구원룸' , '동작구원룸' , '서초구원룸' , '관악구원룸'],
      menus : ['HOME' , 'Products' , 'About'],
      style : 'color : red',
      productJson : [
      {
        porduct : '역삼동원룸',
        price : 60,
        index : 0
      },
      {
        porduct : '마포구원룸',
        price : 90,
        index : 1
      },
      {
        porduct : '동작구원룸',
        price : 100,
        index : 2
      },
      {
        porduct : '서초구원룸',
        price : 50,
        index : 3
      },
      {
        porduct : '관악구원룸' ,
        price : 60,
        index : 4
      }
        
        
    ],
    }
    
  },
  methods : {
    increase() {
      this.신고수[2]++   //만약 신고수라는 변수를 사용하기 위해서는 this 를 붙여줘야 변수로 인식할 수 있습니다.
    }
  },  
  components: {
  }
}
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; 
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  margin-top: 120px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.menu {
    background:  darkslateblue;
    padding: 15px;
    border-radius: 5px;
  }
  .menu a {
    color: white;
    padding : 10px;
  }

  .room-img {
    width: 60%;
    margin-top: 40px;
  }


</style>
