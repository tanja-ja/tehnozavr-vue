<!-- eslint-disable max-len -->
<template>
   <main class="content container" v-if="cartLoading">
          <div class="loader"></div>
        </main>
        <main class="content container"  v-else-if="cartLoadingFailed">
          <button class="loader_btn" @click.prevent="loadCart">Попробуйте обновить страницу</button>
        </main>
     <main class="content container" v-else>
    <div class="content__top">
      <ul class="breadcrumbs">
        <li class="breadcrumbs__item">
          <router-link class="breadcrumbs__link" :to="{name: 'main'}" >
            Каталог
          </router-link>
        </li>
        <li class="breadcrumbs__item">
            <a class="breadcrumbs__link">
              Корзина
          </a>
        </li>
      </ul>

      <h1 class="content__title">
        Корзина
      </h1>
      <span class="content__info">
        {{cartTotal}} товар(а/ов)
      </span>
    </div>
    <section class="cart">
      <form class="cart__form form" action="#" method="POST">
        <div class="cart__field">

          <ul class="cart__list">
            <CartItem v-for="item in products" :key="item.productId" :item="item"/>
          </ul>
        </div>

        <div class="cart__block">
          <p class="cart__desc">
            Мы&nbsp;посчитаем стоимость доставки на&nbsp;следующем этапе
          </p>
          <p class="cart__price">
            Итого: <span>{{totalPrice | numberFormat}} ₽</span>
          </p>

          <router-link v-if="products.length > 0 " tag="button" :to="{name: 'order'}" class="cart__button button button--primery" type="submit">
            Оформить заказ
          </router-link>
        </div>
      </form>
    </section>
  </main>

</template>
<script>
import numberFormat from '@/helpers/numberFormat';
// eslint-disable-next-line object-curly-newline
import { mapGetters, mapState, mapActions } from 'vuex';
import CartItem from '@/components/CartItem.vue';
import gotoPage from '@/helpers/gotoPage';

export default {
  filters: { numberFormat },
  components: { CartItem },
  computed: {
    ...mapGetters({ products: 'cartDetailProducts', totalPrice: 'cartTotalPrice', cartTotal: 'cartTotal' }),
    ...mapState(['cartLoading', 'cartLoadingFailed']),
  },
  methods: {
    gotoPage,
    ...mapActions(['loadCart']),
  },
};
</script>
