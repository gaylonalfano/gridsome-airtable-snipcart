// src/components/BuyButton.vue
<template>
  <button
    class="snipcart-add-item"
    :data-item-id="product.id"
    :data-item-name="product.title"
    :data-item-image="image"
    :data-item-price="product.price"
    :data-item-url="product.path"
  >
    <slot>Buy for {{ product.price }}$</slot>
  </button>
</template>

<script>
export default {
  name: "ProductPreview",
  props: ["product"],
  data() {
    return {
      image: this.product.picture.length
        ? this.product.picture[0].filename
        : null
    };
  }
};
</script>