<template>
  <div class="product-card">
    <div class="custom-badge"><span>Exclusive</span></div>
    <div
      class="display-image"
      :style="{ backgroundImage: `url(https:${hit.image_url}` }"
    ></div>
    <h1 class="name">{{ hit.short_name }}</h1>
    <h3 class="description" v-html="hit.description"></h3>

    <div class="pricing pt-2">
      <div class="d-flex justify-content-between mb-2">
        <p class="price">{{ hit.currency }} {{ price.default }}</p>
        <p v-if="!!getDiscountPercentage()" class="discount-percentage">
          -{{ getDiscountPercentage() }}%
        </p>
      </div>
      <div
        v-if="!!getDiscountPercentage()"
        class="d-flex justify-content-between"
      >
        <p class="discarded-amount">
          <del>{{ hit.currency }} {{ price.default_original }}</del>
        </p>
        <p class="saved-amount">
          Save {{ hit.currency }} {{ price.default_original - price.default }}
        </p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: ["hit"],
  mounted() {
    console.log(this.price, "price");
  },
  data() {
    return {
      price: this.hit.price[this.hit.currency],
    };
  },
  methods: {
    getDiscountPercentage() {
      const {
        default: discountedPrice,
        default_original: originalPrice,
      } = this.price;
      return Math.floor(
        ((originalPrice - discountedPrice) / originalPrice) * 100
      );
    },
  },
};
</script>


<style lang="scss">
.product-card {
  height: 100%;
  background-color: #eeeeee;
  padding: 25px;
  .custom-badge {
    span {
      text-transform: uppercase;
      font-size: 14px;
      font-weight: bold;
      border: 2px solid black;
      border-radius: 7px;
      padding: 2px 4px;
    }
  }
  .display-image {
    height: 320px;
    margin-bottom: 15px;
    background-position: center center;
    background-repeat: no-repeat;
    background-size: contain;
  }
  .name {
    font-size: 18px;
    font-weight: bold;
  }
  .description {
    font-size: 14px;
    color: #7b7b7b;
    font-weight: 600;
  }
  .pricing {
    p {
      margin: 0;
    }
    .price {
      font-size: 18px;
      font-weight: bold;
      color: red;
    }
    .discount-percentage {
      font-size: 14px;
      font-weight: 600;
      background-color: #b3d185;
      border-radius: 4px;
      padding: 4px 5px;
    }
    .discarded-amount {
      font-size: 14px;
      font-weight: 500;
    }
    .saved-amount {
      font-size: 14px;
      font-weight: 600;
    }
  }
}
</style>a   