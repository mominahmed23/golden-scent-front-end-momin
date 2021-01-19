<template>
  <div class="product-card">
    <p>This is a product of perfume</p>
      <b-button variant="success">Button</b-button>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    msg: String
  }
}
</script>


<style lang="scss">
.product-card{
    p {
  color: rgb(251, 255, 22);
}
}

</style>