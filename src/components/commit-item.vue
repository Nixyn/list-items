<template>
 <div class="item">
     <p><a href="">{{commit.id}}</a> - <a href="">{{commit.name}}</a>
     by <a href="">{{commit.user}}</a> at <strong>{{commit.date}}</strong></p>
 </div>
</template>
<script>
/* import axios from 'axios' */
export default {
 name: 'commit-item',
 props: ['commit'],
 watch:{
     'commit': function(){
         alert();
     }
 }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.item>p>a {
 color:red;
 text-decoration: none;
}
</style>