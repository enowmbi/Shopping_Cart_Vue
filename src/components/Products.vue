<template>
<div class='wrapper'>
<div v-bind:key="prod.id" v-for="prod in products">
<Product v-on:add-product-to-cart="$emit('add-product-to-cart',prod)"  v-bind:prod="prod" />
</div>
</div>
</template>

<script>
import Product from '../components/Product.vue'

export default {
name: 'Products',
          components: {
          Product
          },
props: [
"products"
]

}
</script>

<style scoped>
.products{
}
</style>
