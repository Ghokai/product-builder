<template>
  <div class="product-builder">
    <ProductEditor :product="product" class="product-editor"></ProductEditor>
    <ProductPreviewer :product="product"></ProductPreviewer>
  </div>
</template>

<script>
import ProductPreviewer from "./ProductPreviewer.vue";
import ProductEditor from "./ProductEditor.vue";

export default {
  name: "ProductBuilder",
  components: { ProductPreviewer, ProductEditor },
  data: function() {
    return {
      product: {
        imageUrl: "",
        name: "",
        brand: "",
        description: "",
        price: 0.0,
        taxRatio: 0,
        discountRatio: 0
      }
    };
  }
};
</script>


<style scoped>
.product-builder {
  display: flex;
  flex-direction: rows;
  justify-content: center;
  align-items: flex-start;
}
.product-editor {
  margin-right: 30px;
}
</style>