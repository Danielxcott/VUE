<template>
  <nav class="navbar navbar-light sticky-top mr-3">
    <div v-if="cart.length" class=" w-100 navbar-text ml-auto d-flex justify-content-end position-relative">
      <div  class="mr-auto d-flex align-items-end flex-column bd-highlight mb-3 position-absolute" >
        <div class="mb-2">
          <span class="font-weight-bold bg-white"><Curr :amt="cartTotal"></Curr></span>
          <button
              @click="toggleMenu"
              class="btn btn-sm btn-success ml-3"
              id="cartDropdown"
              aria-haspopup="true"
              aria-expanded="false"><i class="fas fa-shopping-cart mr-1"></i>
            {{cartQty}}
          </button>
        </div>
        <Dropdown :cart="cart" :displayCart="displayCart"></Dropdown>
      </div>
    </div>
  </nav>
</template>

<script>
import Curr from "@/components/Curr";
import Dropdown from "@/components/Dropdown";

export default {
  name: "Navbar",
  props:["cart","cartQty","cartTotal"],
  components: {Curr, Dropdown},
  data(){
    return{
      displayCart: false,
    }
  },
  methods:{
    toggleMenu(){
      this.displayCart = !this.displayCart;
    }
  }

}
</script>

<style lang="scss">

</style>