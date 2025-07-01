<script>
import ProductCatalog from '@/views/product-catalog.vue'

export default {
  components: {
    ProductCatalog
  },
  methods: {
    basketElem(elem) {
      this.$emit('basketElem', elem)
    }
  }
}
</script>

<template>
  <ProductCatalog @basketElem="basketElem" />
</template>

<style scoped>

</style>
