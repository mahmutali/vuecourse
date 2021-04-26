<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">Kategori</th>
          <th scope="col">Adı</th>
          <th scope="col">Birim Fiyatı</th>
          <th scope="col">Stok Adedi</th>
          <th scope="col"></th>
        </tr>
      </thead>
      <tr v-for="product in products" :key="product.id">
        <td>{{ product.id }}</td>
        <td>{{ product.categoryId }}</td>
        <td>{{ product.name }}</td>
        <td>{{ product.unitPrice }}</td>
        <td>{{ product.unitsInStock }}</td>
        <td>
          <button type="button" class="btn btn-outline-success" @click="addToCart(product)">
            Sepete ekle
          </button>
        </td>
      </tr>
    </table>
  </div>
</template>


<script>
import { CartItems } from "../models/cartItems";
export default {
  data() {
    return {
      products: [],
    };
  },
  methods: {
    addToCart(product) { 
      if(CartItems.length>0){
        let item = CartItems.find(c=>c.product.id === product.id)

        if(item){
          item.quantity = item.quantity + 1;
        }else{
          CartItems.push({product, quantity:1})
        }
      }else{
         CartItems.push({product, quantity:1})
      }
    },
    async getProducts() {
      const result = await fetch("http://localhost:3000/products");
      const resultToProducts = await result.json();
      this.products = resultToProducts;
    },
    async getProductsByCategory(categoryId) {
      const result = await fetch(
        "http://localhost:3000/products?categoryId=" + categoryId
      );
      const resultToProducts = await result.json();
      this.products = resultToProducts;
    },
    loadPage() {
      if (this.$route.params.id) {
        this.getProductsByCategory(this.$route.params.id);
      } else {
        this.getProducts();
      }
    },
  },
  mounted() {
    this.loadPage();
  },
  watch: {
    $route() {
      this.loadPage();
    },
  },
};
</script>


<style>
</style>