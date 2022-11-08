<template>
  
  <div v-for="(i, p) in 원룸들" :key="p">
    <!-- <p>{{p}}</p> -->
    <img :src="원룸들[p].image" class="room-img">
    <h4 >{{원룸들[p].title}}</h4> <!--@click="openModal = true; clickCheck=p"-->
    <p>{{원룸들[p].price}}원</p>
 </div>

</template>

<script>
export default {
    name  : 'card',
    props : {
        원룸들 : Array,
    }
}
</script>

<style>

</style>