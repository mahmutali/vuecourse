<template>
  <div>
    <table class="table">
      <tr v-for="product in products" :key="product.id">
        <td>{{ product.id }}</td>
        <td>{{ product.categoryId }}</td>
        <td>{{ product.name }}</td>
        <td>{{ product.unitPrice }}</td>
        <td>{{ product.unitsInStock }}</td>
      </tr>
    </table>
  </div>
</template>


<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  methods: {
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