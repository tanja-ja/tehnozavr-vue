<!-- eslint-disable vue/no-mutating-props -->
<!-- eslint-disable no-undef -->
<!-- eslint-disable vue/no-parsing-error -->
<!-- eslint-disable vue/valid-v-model -->
<!-- eslint-disable max-len -->
<!-- eslint-disable vuejs-accessibility/label-has-for -->
<template>
  <li class="catalog__item">
            <router-link class="catalog__pic" :to="{name: 'product', params: {id: product.id}}" >
              <img :src="product.image"  :alt="product.title" v-bind:width="product.width">
            </router-link>
            <h3 class="catalog__title">
              <a href="#">
                {{product.title}}
              </a>
            </h3>

            <span class="catalog__price">
              {{product.price | numberFormat}} ₽
            </span>

            <ul class="colors colors--black">
              <li class="colors__item" v-for="color in product.colors" :key="color.id" >
                <label class="colors__label" >
                  <input class="colors__radio sr-only" type="radio" :value="color" v-model="color1">
                  <span class="colors__value" :style="{'background-color': color.code, 'border': fontSize + 'px', borderStyle } ">
                  </span>
                </label>
              </li>
            </ul>
          </li>
</template>

<script>
import gotoPage from '@/helpers/gotoPage';
import numberFormat from '@/helpers/numberFormat';
import router from '@/router';
// import axios from 'axios';

export default {
  data() {
    return {
      color1: this.product.colors[0],
      fontSize: 1,
      borderStyle: 'solid',
    };
  },
  filters: {
    numberFormat,
  },
  methods: {
    gotoPage,
  },
  props: ['product'],
  // eslint-disable-next-line vue/no-unused-components
  components: { router },
};
</script>
<style>
.catalog__pic img {
    object-fit: unset;
}
</style>
