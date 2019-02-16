<template>
<div class="header">
<h1> E-Commerce Inc. |</h1>
<a href='' v-on:click="$emit('showGrid')"> Grid </a>
<a href='' v-on:click="$emit('showList')"> List </a>
</div>
</template>

<script>
export default {
name: 'Header'
}
</script>

<style scoped>
.header{
    background: #555;
    color: #fff;
    margin-bottom: 20px;
}

a{
        text-decoration: none;
        color: #fff;
}
a:hover{

  text-transform: bold;
  }
</style>
