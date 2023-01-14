<!-- eslint-disable vue/no-parsing-error -->
<!-- eslint-disable max-len -->
<template>
 <ul class="catalog__list">
    <ProductItem :product="product" v-for="product in products" :key="product.id" ></ProductItem>
        </ul>
</template>
<script>
import ProductItem from './ProductItem.vue';

export default {
  components: { ProductItem },
  props: ['products'],
};
</script>
