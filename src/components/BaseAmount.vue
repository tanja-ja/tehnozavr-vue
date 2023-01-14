<!-- eslint-disable no-undef -->
<!-- eslint-disable vuejs-accessibility/form-control-has-label -->
<!-- eslint-disable max-len -->
<template>
          <div class="form__counter">
                <button type="button" aria-label="Убрать один товар" @click.prevent="decrementAmount()">
                  <svg width="12" height="12" fill="currentColor">
                    <use xlink:href="#icon-minus"></use>
                  </svg>
                </button>
                <input type="text" v-model.number="productAmount" :amount="productAmount">
                <button type="button" aria-label="Добавить один товар" @click.prevent="incrementAmount()">
                  <svg width="12" height="12" fill="currentColor">
                    <use xlink:href="#icon-plus"></use>
                  </svg>
                </button>
              </div>
</template>
<script>
export default {
  model: {
    prop: 'productAmount',
    event: 'changeAmout',
  },
  props: ['amount'],
  data() {
    return {
      productAmount: this.amount,
    };
  },
  methods: {
    decrementAmount() {
      if (this.productAmount > 1) {
        this.$emit('changeAmout', this.productAmount -= 1);
      }
    },
    incrementAmount() {
      this.$emit('changeAmout', this.productAmount += 1);
    },
  },
};
</script>
