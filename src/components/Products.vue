<template>
  <div class="products-page">
    <h1 class="text-center">Golden Scent</h1>
    <h2 class="text-center ">Products</h2>
    <b-container class="pt-4">
      <div class="text-center pt-4" v-if="loading">
      <b-spinner style="width: 4rem; height: 4rem;"  variant="primary" type="grow" label="Spinning"></b-spinner>
      </div>
      <b-row v-if="hits">
        <b-col cols="12" sm="6" md="6" lg="4" xl="3" class="mb-4" v-for="hit in hits" :key="hit.objectID"> <productCard :hit="hit" /></b-col>
      </b-row>

</b-container>
   
  </div>
</template>

<script>
import axios from 'axios'
import ProductCard from './ProductCard.vue'
export default {
  components: { ProductCard },
  name: 'Products',
    data () {
    return {
      hits: null,
      loading: true,
      errored: false
    }
  },
    mounted () {
    axios
      .get('https://gs-euw1-public-data-prod.s3-eu-west-1.amazonaws.com/new-web/test/test.json')
      .then(response => {
        console.log(response.data);
        this.hits = response.data.hits
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
  }
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
