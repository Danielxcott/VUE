<template>
 <navbar :cart="cart" :cart-total="cartTotal" :cart-qty="cartQty" @delete-item="deleteItem"></navbar>
  <div class="container">
    <router-view :products="products" :cart="cart" @addItem="addItem" @delete-item="deleteItem" :cart-total="cartTotal"/>
  </div>
</template>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";


</style>
<script>
import Navbar from "@/components/Navbar";
export default {
  components: {Navbar},
  // props:["products"],
  data() {
    return {
      cart: [],
      products : [],
      displayCart: false,
    }
  },
  created() {
    fetch("https://hplussport.com/api/products/order/price")
        .then(response => response.json())
        .then(data => {
          console.log(data)
          this.products = data;
        });
  },
  methods: {
  addItem(product){
    let whichproduct;
    let exiting = this.cart.filter((x,y)=>{
      if(x.product.id == Number(product.id)){
        console.log(y);
        console.log(x);
        whichproduct = y;
        return true;
      }else{
        return false;
      }
    })
    if(exiting.length){
      this.cart[whichproduct].qty++
    }else{
    this.cart.push({product:product,qty:1})
    }
  },
    deleteItem:function (id){
    if(this.cart[id].qty>1){
      this.cart[id].qty--
    }else{
      this.cart.splice(id,1)
    }
    }
  },
  computed:{
    cartTotal(){
      let sum = 0;
      for(let key in this.cart){
        sum = sum+ this.cart[key].product.price * this.cart[key].qty
      }
      return sum
    },
    cartQty(){
      let qty = 0;
      for(let key in this.cart){
        qty = qty + this.cart[key].qty
      }
      return qty;
    }
  }
}
</script>