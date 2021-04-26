<template lang="">
    <li class="nav-item dropdown">
            <a
              class="nav-link dropdown-toggle"
              href="#"
              id="navbarDropdown"
              role="button"
              data-bs-toggle="dropdown"
              aria-expanded="false"
            >
              Dropdown
            </a>
            <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
              <li  v-for="cartItem in cartItems" :key="cartItem.product.id">
                  <a class="dropdown-item">
                      {{cartItem.product.name}}
                      <span class="badge bg-primary">{{cartItem.quantity}}</span>   
                </a>
             </li>
              <li><hr class="dropdown-divider" /></li>
              <li><a class="dropdown-item" href="#">Something else here</a></li>
            </ul>
          </li>
</template>
<script>
import { CartItems } from "../models/cartItems";
export default {
  data() {
    return {
      cartItems: [],
    };
  },
  mounted() {
    this.cartItems = CartItems;
  },
};
</script>
<style lang="">
</style>