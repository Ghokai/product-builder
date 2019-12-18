<template>
  <div class="product-previewer">
    <div class="product-image">
      <img v-if="!product.imageUrl" alt="NA" src="../assets/placeholder-img.jpg" />
      <img v-else :src="product.imageUrl" />
    </div>
    <div class="product-name">
      <span v-if="product.name.length>0">{{product.name}}</span>
      <span v-else>&lt;name&gt;</span>
    </div>
    <div class="product-brand">
      <span v-if="product.brand.length>0">{{product.brand}}</span>
      <span v-else>&lt;brand&gt;</span>
    </div>
    <div class="product-description">
      <span>{{product.description}}</span>
    </div>
    <div class="product-price">
      <span class="product-price-span" v-if="product.price>0">ab {{finalPrice}} €</span>
      <span class="product-price-span" v-else>ab ##,## €</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductPreviewer",
  props: {
    product: {
      type: Object
    }
  },
  computed: {
    finalPrice() {
      //add tax
      let calculatedPrice =
        parseInt(this.product.price) +
        (this.product.price * this.product.taxRatio) / 100;
      //substract discount
      calculatedPrice =
        calculatedPrice * ((100.0 - this.product.discountRatio) / 100);
      return Number.parseFloat(calculatedPrice).toFixed(2);
    }
  }
};
</script>

<style scoped>
.product-previewer {
  margin: 10px;
  padding: 20px;
  width: 350px;
  display: flex;
  flex-direction: column;
  border: 3px solid teal;
  border-radius: 5px;
}

.product-image {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  max-height: 250px;
  min-height: 250px;
}
img {
  max-width: 250px;
  height: auto;
}
.product-name {
  vertical-align: middle;
  height: 20px;
  padding: 10px 10px;
  font-size: 20px;
  font-weight: 600;
  color: teal;
  text-align: center;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
}

.product-brand {
  text-align: center;
  vertical-align: middle;
  color: #a9a9a9;
  height: 20px;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  font-size: 16px;
}

.product-description {
  display: inline-block;
  vertical-align: top;
  background: #f6f6f6;
  border: 1px solid #bdbdbd;
  border-radius: 4px;
  padding: 0.5rem;
  line-height: 1.4;
  height: 120px;
  max-height: 120px;
  overflow-x: hidden;
  overflow-y: scroll;
  text-overflow: ellipsis;
  margin-bottom: 1rem;
}

.product-price-span {
  float: right;
  color: black;
  font-size: 20px;
  font-weight: 600;
}
</style>