<template>
  <div id="app">
    <div class="container">
      <navi />
      <div class="row">
        <div class="col-md-3"><category-list /></div>
        <div class="col-md-9"><router-view /></div>
      </div>
    </div>
  </div>
</template>
<script>
import  CategoryList  from "./components/CategoryList";
import  Navi  from "./components/Navi";
export default {
  name:"app",
  components:{
    CategoryList,Navi}
}
</script>
<style>
</style>
