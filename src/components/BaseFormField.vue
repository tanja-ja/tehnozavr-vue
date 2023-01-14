<!-- eslint-disable max-len -->
<!-- eslint-disable vuejs-accessibility/label-has-for -->

<template>
  <label class="form__label">
    <slot/>
      <!-- <input class="form__input" v-model="formData.name" type="text" name="name" placeholder="Введите ваше полное имя"> -->
      <span class="form__value">{{ title }}</span>
      <span class="form__error" v-if="error">{{ error }}</span>
  </label>
</template>

<script>
export default {
  props: ['title', 'error'],
};
</script>
