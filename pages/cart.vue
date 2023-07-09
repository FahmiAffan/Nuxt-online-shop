<template>
  <div></div>
</template>

<script>
export default {
  name: 'CartPages',
  mounted() {
    this.$axios
      .$get('https://fakestoreapi.com/carts')
      .then((response) => (this.produk = response))
      .catch((error) => console.log(error))
  },
}
</script>

<style>
</style>
