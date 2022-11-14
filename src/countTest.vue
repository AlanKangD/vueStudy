<template>


<div class="black-bg" v-if="openModal == true">
    <div class="white-bg"> 
     
      <img :src="원룸들[clickCheck].image" class="room-img">
      <h4>{{원룸들[clickCheck].title}}</h4>
      <p>{{원룸들[clickCheck].content}}</p>
      <p>{{원룸들[clickCheck].price}}원</p>
      
      <!-- <button @click="openModal=false">닫기</button> -->
    </div>
  </div>
</template>

<script>

export default {
    name : 'Discount',
    props : {
      원룸들 : Array,
      openModal : Boolean,
      clickCheck : Number,

    },
    
}
</script>

<style>
 
</style>