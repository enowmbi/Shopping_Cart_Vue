<template>
  <div id="app">
  <Header v-on:showGrid="displayGrid" v-on:showList="displayList"/>
  <div class="container-fluid">
<div class="row">
<div class="col-md-9">
  <Products v-on:add-product-to-cart="addProduct($event)" v-bind:products="products" />
</div>
<div class="col-md-3">
<ShoppingCart v-bind:shoppingCartItems="shoppingCartItems"/>
</div>
</div>
</div>
  <Footer />
  </div>
</template>

<script>
import Header from './components/layout/Header.vue'
import Products from './components/Products.vue'
import ShoppingCart from './components/ShoppingCart.vue'
import Footer from './components/layout/Footer.vue'

export default {
  name: 'app',
  components: {
    Header,
    Products,
    ShoppingCart,
    Footer
  },

  data(){
  return{
products: [
          {id: 1,name:"Macbook Air",description:"The original Macbook Air 14 inch",price:1999,instock: 50},
          {id: 2,name:"Samsung Galaxy Note 4",description:" 8GB storage and 2GB memory",price:200,instock: 22},
          {id: 3,name:"Hisense 65 inch TV",description:"65 inch 4K LED TV for entertainment",price:1850,instock: 12},
          {id: 4,name:"Sony 6.1 sound system",description:"Dolby Digital 6.1 sound system",price:500,instock: 5},
          {id: 5,name:"Macbook Air",description:"The original Macbook Air 14 inch",price:1250,instock: 10},
          {id: 6,name:"Macbook Air",description:"The original Macbook Air 14 inch",price:150,instock: 3},
          {id: 7,name:"Macbook Air",description:"The original Macbook Air 14 inch",price:210,instock: 0},
          {id: 8,name:"Macbook Air",description:"The original Macbook Air 14 inch",price:250,instock: 12},




],
shoppingCartItems: []
  }
  },

methods: {
          displayGrid() {
                alert("show Grid has been bubbled !");
          },

          displayList() {
                alert("Show List has been bubbled !");
          },
          addProduct(prod){
              this.shoppingCartItems = [...this.shoppingCartItems, prod];
}

          }

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  /* color: #2c3e50; */
  /* margin-top: 0px; */
}
.wrapper {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;
  grid-auto-rows: 300px 300px;

}
</style>
