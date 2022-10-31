<template>

  <div class="menu">
    <a v-for="menu in menus" :key="menu"> {{ menu }} </a>
    
  </div>

  <div v-for="produnct in productJson" :key="produnct.index">
    <p>글번호 : {{produnct.index}}</p>
    <h4>{{ produnct.porduct }}</h4>
    <p>{{ produnct.price }} 만원</p>
  </div> 
  
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
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
.menu {
    background:  darkslateblue;
    padding: 15px;
    border-radius: 5px;
  }
  .menu a {
    color: white;
    padding : 10px;
  }
</style>
