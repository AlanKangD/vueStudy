<template>
 
<!-- <div class="start" :class="{ end : openModal }"> -->
<transition name="fade">
<div class="black-bg" v-if="openModal == true">
    <div class="white-bg"> 
     
      <img :src="원룸들[clickCheck].image" class="room-img">
      <h4>{{원룸들[clickCheck].title}}</h4>
      <p>{{ 원룸들[clickCheck].content}}</p>
      <p> {{ month }} 개월 선택함 : {{원룸들[clickCheck].price * month}}원</p>
      <!-- <input  @input="month = $event.target.value"> <br> -->
      <input v-model.number="month"> <br>
      
       <button @click="openModal=false">닫기</button> 
    </div>
  </div>
</transition>
<!-- </div> -->
  <discountTest :원룸들="원룸들" :clickCheck="clickCheck"/>
  
  <div class="menu">
    <a v-for="menu in menus" :key="menu"> {{ menu }} </a>  
  </div> 

 <discount v-if="showdiscount" />

 <button @click="priceSort">가격순 버튼</button>
 <button @click="sortBack">되돌리기</button>
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
import discount from './discount.vue';

export default {
  name: 'App',
  data() {
    return {
      showdiscount : true,
      원룸들오리지널 : [...data],
      month : "",
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
  watch : {
    month(a , b) { // a는 변경 후 b는 변경 전 데이터 입니다. 
      console.log(isNaN(a));
      // if(isNaN(a) == true) {
      //   alert('문자열을 입력했습니다');
      //   this.month = "";
      // }
      if(typeof a == "string") {
        this.month = ""
        alert('숫자만 들어올 수 있습니다!')
      }
      if(a > 13) {
        this.month = ""
        alert('13보다 입력값이 큽니다!' + b)
        
      }
    }
  },
  methods : {
    increase() {
      this.신고수[2]++   //만약 신고수라는 변수를 사용하기 위해서는 this 를 붙여줘야 변수로 인식할 수 있습니다.
    },
    priceSort() {
      this.원룸들.sort(function(a,b) {
        return a.price - b.price
      }) 
    },
    sortBack() {
      this.원룸들 = [...this.원룸들오리지널];
    }
  },  
  mounted(){
   setTimeout(()=>{
      this.showdiscount = false;
   }, 2000);
  },

  components: {
    discountTest : discountTest,
    card : card,
    discount : discount,
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

.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

.fade-enter-from {
  opacity: 0;

}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;

}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
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
