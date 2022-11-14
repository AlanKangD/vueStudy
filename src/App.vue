<template>
 

<div class="black-bg" v-if="openModal == true">
    <div class="white-bg"> 
     
      <img :src="원룸들[clickCheck].image" class="room-img">
      <h4>{{원룸들[clickCheck].title}}</h4>
      <p>{{ 원룸들[clickCheck].content}}</p>
      <p> {{ month }} 개월 선택함 : {{원룸들[clickCheck].price * month}}원</p>
      <!-- <input  @input="month = $event.target.value"> <br> -->
      <input  v-model.number="month"> <br>
      <textarea v-model.number="month"></textarea>   <!--v-model 또는 @input 을 쓰면 됩니다. -->
      <select v-model.number="month">
        <option>123</option>
        <option>456</option>
        <option>789</option>
      </select>
      <input type="checkbox" @change="month = 1">

       <button @click="openModal=false">닫기</button> 
    </div>
  </div>

  <discountTest :원룸들="원룸들" :clickCheck="clickCheck"/>

  

  <div class="menu">
    <a v-for="menu in menus" :key="menu"> {{ menu }} </a>  
  </div>
  <div class="discount">
          <h4>지금 결제하면 20% 할인</h4>
  </div>  
  <card @openMsg="openModal = true; clickCheck = $event;" :원룸들="원룸들" />


 <br>
  <button v-on:click="신고수[0]++">허위매물신고</button> <span>신고 수 : {{신고수}}</span>
  <button v-on:mouseover="신고수[1]++">허위매물신고</button> <span>신고 수 : {{신고수}}</span>
  <button v-on:mouseover="increase()">허위매물신고</button> <span>신고 수 : {{신고수}}</span>  <!--vue 함수 만드는 방법-->
  
</template>

<script>
import data from './assets/data';
import discountTest from './countTest.vue';
import card from './card.vue';

export default {
  name: 'App',
  data() {
    return {
      month : 1,
      오브잭트 : { name : 'kim' , age : 20},
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
    discountTest : discountTest,
    card : card,
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

  .discount {
    background: #eee;
    padding: 10px;
    margin: 10px;
    border-radius: 5px;
  }

</style>
