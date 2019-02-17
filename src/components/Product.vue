<template>
<div class='product'>
    <div class="card-deck mb-3 text-center">
        <div class="card mb-2 shadow-sm">
          <div class="card-header">
            <h4 class="my-0 font-weight-normal">{{ prod.name }}</h4>
          </div>
          <div class="card-body">
            <h1 class="card-title pricing-card-title">{{ prod.price | currency }} </h1>
            <ul class="list-unstyled mt-3 mb-4">
              <li>{{ prod.description }}</li>
              <li>{{ prod.instock }} in stock</li>
              <li>Quantity: <input type="text" v-model="qty"/></li>
              </ul>
              <button v-on:click="addProductToCart" type="button" class="btn btn-lg btn-block btn-outline-primary">Add to Cart</button>
            <!-- <button v-on:click="$emit('add-product-to-cart',prod)" type="button" class="btn btn-lg btn-block btn-outline-primary">Add to Cart</button> -->
            </div>
            </div>
          </div>
        </div>
        </div>
</div>
</template>

<script>
export default {
name: 'Product',
          props: [
          "prod"
          ],
    data(){
        return{
        qty: 1
        }
    },

    methods:{
        addProductToCart(){
            const purchasedProduct = {
                id: this.prod.id,
                name: this.prod.name,
                description: this.prod.description,
                price: this.prod.price,
                quantity: this.qty,
                extendedPrice: this.qty * this.prod.price
                
            }
console.log(purchasedProduct);
            //emit to the parent which passes to shopping cart
            this.$emit('add-product-to-cart',purchasedProduct)
        }
    
    },

filters: {
currency: function(value){
          var formatter = new Intl.NumberFormat("en-US",{
style: "currency",currency:'usd',minimumFractionDigits: 0});
          return formatter.format(value);
          }
      },
    
 }
</script>

<style scoped>
.product{
}
</style>
