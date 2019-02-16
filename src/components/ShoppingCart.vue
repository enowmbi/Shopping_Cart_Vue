<template>
<div class="shoppingcart">
<div class="row">
        <div class="col-12">
          <h4 class="d-flex  justify-content-between align-items-center mb-3">
            <span class="text-muted">Your cart</span>
            <span class="badge badge-secondary badge-pill">{{ shoppingCartItems.length   }} item(s)</span>
          </h4>
          <ul class="list-group mb-3">
            <li v-for="item in shoppingCartItems" class="list-group-item d-flex justify-content-between lh-condensed">
              <div>
                <h6 class="my-0"> {{ item.name }}</h6>
                <small class="text-muted">{{ item.description }}</small>
              </div>
              <span class="text-muted">{{ item.price | currency }}</span>
            </li>

            <li class="list-group-item d-flex justify-content-between">
              <span>Total (USD)</span>
              <strong>{{ shoppingCartTotal |currency }}</strong>
            </li>
          </ul>

        </div>
    </div>
</div>
</template>

<script>
export default {
name: 'ShoppingCart',
          props:["shoppingCartItems"],

          filters: {
            currency: function(value){
              var formatter = new Intl.NumberFormat("en-US",{
            style: "currency",currency:'usd',minimumFractionDigits: 0});
          return formatter.format(value);
          }
      },
computed: {
          shoppingCartTotal(){
           var total =0;
          //iterate through the items in the shopping cart and calculate the total
          //it is updated as items are added or removed from the cart - hence computed property
   this.shoppingCartItems.forEach(function(item) {
             total += item.price;
           });
       return total;
}
          }
          }



</script>

<style scoped>
.shoppingcart{
}
</style>
