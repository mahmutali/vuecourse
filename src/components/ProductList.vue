<template>
  <div>
    <table class="table">
      <tr v-for="product in products" :key="product.id">
        <td>{{product.id}}</td>
        <td>{{product.categoryId}}</td>
        <td>{{product.name}}</td>
        <td>{{product.unitPrice}}</td>
        <td>{{product.unitsInStock}}</td>
      </tr>
    </table>
  </div>
</template>


<script>
export default {
   data() {
     return {
       products:[
         {id:1,categoryId:1, name:"Laptop 1",unitPrice:15000, unitsInStock:9},
         {id:2,categoryId:1, name:"Laptop 2",unitPrice:16000, unitsInStock:9},
         {id:3,categoryId:2, name:"Laptop 3",unitPrice:15000, unitsInStock:9},
         {id:4,categoryId:2, name:"Laptop 4",unitPrice:15000, unitsInStock:9},
         {id:5,categoryId:3, name:"Laptop 5",unitPrice:15000, unitsInStock:9},
       ]
     }
   },

};
</script>


<style>
</style>