<template>
  <div>
    <h1>Products Page</h1>
    <product-card />
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue'
export default {
  components: { ProductCard },
  name: 'Products',
  props: {
    msg: String
  }
}
</script>


<style>
h1 {
  color: blueviolet;
}
</style>
