<template>
  <div class="product-card">
      <div class="custom-badge"><span>Exclusive</span></div>
    <div class="display-image" :style="{backgroundImage: `url(https:${hit.image_url}`}"></div>
    <h1 class="name">{{hit.name}}</h1>
    <h3 class="description">Lorem ipsum dolor sit amet consectetur adipisicing elit. Sit officiis, magni velit, a, volup!</h3>

     <div class="pricing pt-2">
         <div class="d-flex justify-content-between mb-2">
             <p class="price">{{hit.currency}} {{hit.special_price}}</p>
             <p class="discount-percentage">-20%</p>
         </div>
         <div class="d-flex justify-content-between">
             <p class="discarded-amount"><del>{{hit.currency}} 150</del></p>
             <p class="saved-amount">Save {{hit.currency}} 30</p>
         </div>
     </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: ["hit"],
     mounted () {
      console.log(this.hit);
  }
}
</script>


<style lang="scss">
.product-card{
    height: 100%;
    background-color: #eeeeee;
    padding: 25px;
    .custom-badge{
        span{
            text-transform: uppercase;
            font-size: 14px;
            font-weight: bold;
            border: 2px solid black;
            border-radius: 7px;
            padding: 2px 4px;
        }
    }
    .display-image{
        height: 320px;
        margin-bottom: 20px;
        background-position: center center;
        background-repeat: no-repeat;
        background-size: contain;
    }
    .name{
        font-size: 18px;
        font-weight: bold;
    }
    .description{
        font-size: 14px;
        color: #7b7b7b;
        font-weight: 600;
    }
    .pricing{
        p{
            margin: 0;
        }
        .price{
            font-size: 18px;
            font-weight: bold;
            color: red;
        }
        .discount-percentage{
            font-size: 14px;
            font-weight: 600;
            background-color: #b3d185;
            border-radius: 4px;
            padding: 4px 5px;
        }
        .discarded-amount{
            font-size: 14px;
            font-weight: 500;
        }
        .saved-amount{
            font-size: 14px;
            font-weight: 600;
        }
    }

}

</style>