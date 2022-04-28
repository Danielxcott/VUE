<template>
  <div class="home">


    <section class="container">
      <RangeSelector :products="filteredProducts" v-model="max"></RangeSelector>
      <product-list :products="filteredProducts"></product-list>
    </section>
  </div>
</template>

<script>

import RangeSelector from "@/components/RangeSelector";
import ProductList from "@/components/ProductList";
export default {

  name: 'HomeView',
  props:["products"],
  components: {
  RangeSelector ,ProductList
  },
  data() {
    return {
      max: 50,
      cart: [],
    }
  },

  computed: {
    filteredProducts() {
      return this.products.filter( item => (item.price < Number(this.max)))
    }

  },


}
</script>
<style>



</style>
