<template>
  <transition-group name="products" appear>
    <div v-for="item in products" :key="item.id" id="item-list" class="row align-items-center">
      <Product :item="item"></Product>
    </div>
  </transition-group>
</template>

<script>
import Product from "@/components/Product";

export default {
  props:["products"],
  name: "ProductList",
  components: {Product},

}
</script>

<style lang="scss">
.products-enter-active,
.products-leave-active {
  transition: all .5s ease-in-out;
}

.products-enter-from {
  opacity: 0;
  transform:translateX(300px);
}

.products-leave-to {
  opacity: 0;
  transform: translateX(-300px);
}
</style>