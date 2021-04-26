<template>
  <ul class="list-group">
    <li class="list-group-item" v-for="category in categories" :key="category.id">
        <router-link :to="{name:'ProductListByCategory',params:{id:category.id}}">
            {{category.name}}
        </router-link>
       
    </li>
  </ul>
</template>
<script>
export default {
   data() {
     return {
       categories:[]
     }
   },
   methods:{
     async getCategories(){
       const result = await fetch("http://localhost:3000/categories");
       const resultToCategories = await result.json();
       this.categories = resultToCategories;
     }
   },
   mounted(){
     this.getCategories();
   }
};
</script>
<style>
</style>