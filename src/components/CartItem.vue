<!-- eslint-disable vue/no-computed-properties-in-data -->
<!-- eslint-disable vue/no-dupe-keys -->
<!-- eslint-disable vuejs-accessibility/form-control-has-label -->
<!-- eslint-disable max-len -->
<template>
     <li class="cart__item product">
              <div class="product__pic">
                <img :src="item.product.image" width="120" height="120"  alt="item.product.title">
              </div>
              <h3 class="product__title">
               {{item.product.title}}
              </h3>
              <span class="product__code">
                Артикул: {{item.product.id}}
              </span>
              <BaseAmount v-model="amount" :amount="amount"/>
              <b class="product__price">
                {{(item.amount * item.product.price) | numberFormat}} ₽
              </b>

              <button class="product__del button-del" type="button" aria-label="Удалить товар из корзины" @click.prevent="deleteCart()">
                <svg width="20" height="20" fill="currentColor">
                  <use xlink:href="#icon-close"></use>
                </svg>
              </button>
            </li>
</template>

<script>
import numberFormat from '@/helpers/numberFormat';
// import { mapMutations } from 'vuex';
import BaseAmount from './BaseAmount.vue';

export default {
  components: { BaseAmount },
  data() {
    return {
      // eslint-disable-next-line no-undef, vue/no-computed-properties-in-data
      productAmount: this.amount,
    };
  },
  filters: { numberFormat },
  props: ['item'],
  computed: {
    amount: {
      get() {
        return this.item.amount;
      },
      set(value) {
        this.$store.dispatch('updateCartProductAmount', { productId: this.item.productId, amount: value });
      },
    },
  },
  methods: {
    // ...mapMutations({ deleteProduct: 'deleteCartProduct' }),
    deleteCart() {
      this.$store.dispatch('deleteCartProductAmount', this.item.productId);
    },
  },
};
</script>
