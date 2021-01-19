<template>
  <div class="products-page">
    <h1 class="text-center">Golden Scent</h1>
    <h2 class="text-center products">Products</h2>
    <b-container class="pt-4">
      <div class="text-center pt-4" v-if="loading">
        <b-spinner
          style="width: 4rem; height: 4rem"
          variant="primary"
          type="grow"
          label="Spinning"
        ></b-spinner>
      </div>
      <div class="text-center pt-5" v-if="errored">
        <h2 class="text-center mt-3 text-warning">
          Something Went Wrong! Try Again
        </h2>
        <b-button variant="outline-primary" v-on:click="fetchData"
          >Try Again</b-button
        >
      </div>
      <b-row v-if="hits && hits.length">
        <b-col
          cols="12"
          sm="6"
          md="6"
          lg="4"
          xl="3"
          class="mb-4"
          v-for="hit in hits"
          :key="hit.objectID"
        >
          <productCard :hit="hit"
        /></b-col>
      </b-row>
      <h2 v-else class="text-center">
        {{ loading ? "Loading" : "No" }} Products
      </h2>
    </b-container>
  </div>
</template>

<script>
import axios from "axios";
import ProductCard from "./ProductCard.vue";
export default {
  components: { ProductCard },
  name: "Products",
  data() {
    return {
      hits: null,
      loading: false,
      errored: false,
    };
  },
  methods: {
    fetchData() {
      this.loading = true;
      this.errored = false;
      axios
        .get(
          "https://gs-euw1-public-data-prod.s3-eu-west-1.amazonaws.com/new-web/test/test.json"
        )
        .then((response) => {
          this.loading = false;
          this.errored = false;
          this.hits = response.data.hits;
        })
        .catch((error) => {
          console.log(error);
          this.errored = true;
          this.loading = false;
        });
    },
  },
  mounted() {
    this.fetchData();
  },
};
</script>


<style lang="scss">
.products-page {
  padding-top: 50px;
  .products {
    color: #faa7b5;
  }
}
</style>
