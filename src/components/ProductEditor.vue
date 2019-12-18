<template>
  <div class="product-editor">
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-name">Product Name</label>
      <input
        name="product-name"
        class="editor-form-element-input"
        v-model="product.name"
        @input="update(product, 'name', $event)"
        type="text"
      />
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-brand">Product Brand</label>
      <input
        name="product-brand"
        class="editor-form-element-input"
        v-model="product.brand"
        @input="update(product, 'brand', $event)"
        type="text"
      />
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-image">Product Image Url</label>
      <input
        name="product-image"
        class="editor-form-element-input"
        v-model="product.imageUrl"
        @input="update(product, 'imageUrl', $event)"
        type="text"
      />
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-description">Product Description</label>
      <textarea
        name="product-description"
        class="editor-form-element-input editor-form-element-text-area"
        @input="update(product, 'description', $event)"
        rows="6"
        v-model="product.description"
      ></textarea>
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-price">Product Price</label>
      <input
        name="product-price"
        class="editor-form-element-input"
        v-model="product.price"
        @input="update(product, 'price', $event)"
        type="number"
        min="0.00"
        max="10000.00"
        step="0.01"
      />
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-tax">Product Tax Ratio</label>
      <input
        name="product-tax"
        class="editor-form-element-input"
        v-model="product.taxRatio"
        @input="update(product, 'taxRatio', $event)"
        type="number"
        min="0"
        max="100"
        step="1"
      />
    </div>
    <div class="editor-form-element">
      <label class="editor-form-element-label" for="product-discount">Product Discount Ratio</label>
      <input
        name="product-discount"
        class="editor-form-element-input"
        v-model="product.discountRatio"
        @input="update(product, 'discountRatio', $event)"
        type="number"
        min="0"
        max="100"
        step="1"
      />
    </div>
  </div>
</template>

<script>
import Vue from "vue";
export default {
  name: "ProductEditor",
  props: {
    product: {
      type: Object
    }
  },
  methods: {
    update: function(obj, prop, event) {
      Vue.set(obj, prop, event.target.value);
    }
  }
};
</script>

<style>
.product-editor {
  width: 400px;
}
.editor-form-element {
  margin-bottom: 10px;
}
.editor-form-element-label {
  font-size: 14px;
  margin-bottom: 5px;
  font-weight: 500;
  color: #0e4c92;
  width: 100%;
  display: block;
  user-select: none;
}
.editor-form-element-input {
  width: 90%;
  height: 30px;
  border-radius: 5px;
  box-shadow: none;
  border: 1px solid #ced6e0;
  transition: all 0.3s ease-in-out;
  font-size: 18px;
  padding: 5px 10px;
  background: none;
  color: #1a3b5d;
  font-family: "Source Sans Pro", sans-serif;
}
.editor-form-element-text-area {
  height: 140px;
}
</style>