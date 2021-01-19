<template>
  <div class="products-page">
    <h1 class="text-center">Golden Scent</h1>
    <h2 class="text-center ">Products</h2>
    <b-container class="pt-4">
  <b-row>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
    <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4"> <productCard /></b-col>
   
  </b-row>

</b-container>
   
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue'
export default {
  components: { ProductCard },
  name: 'Products',
}
</script>


<style lang="scss">
.products-page{
  padding-top: 50px;
   h2{
    color: #faa7b5;
  }
 
}
</style>
