<!-- eslint-disable max-len -->
<!-- eslint-disable vue/multi-word-component-names -->
<template>
    <router-link  class="header__cart" :to="{name: 'cart'}" aria-label="Корзина с товарами">
        <svg width="30" height="21" fill="currentColor">
            <use xlink:href="#icon-cart"></use>
        </svg>
        <span v-if="cartLoading"  class="loader-cart" ></span>
        <span v-else class="header__count" aria-label="Количество товаров">{{ $store.state.cartProducts.length }}</span>
    </router-link>
    </template>

<script>
import { mapState } from 'vuex';

export default {
  computed: {
    ...mapState(['cartLoading']),
  },
};
</script>
<style>

.header__cart {
    position: relative;
}
.loader-cart {
  width: 15px;
  height: 15px;
  border-radius: 50%;
  display: inline-block;
  position: absolute;
  top:-3px;
  left:25px;
  background: linear-gradient(0deg, rgba(54, 138, 79, 0.2) 33%, #9eff00 100%);
  box-sizing: border-box;
  animation: rotation 1s linear infinite;
}
.loader-cart::after {
  content: '';
  box-sizing: border-box;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #222;
}
@keyframes rotation {
  0% { transform: rotate(0deg) }
  100% { transform: rotate(360deg)}
}
</style>
