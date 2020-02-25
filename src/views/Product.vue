<template>
  <div>
    <h1>This is the id {{ $route.params.id }}</h1>
    <ProductInfo :product="product">
      <template v-slot:title>
        <h1>{{ product.title }}</h1>
      </template>
    </ProductInfo>
    <button @click="edit">Edit Product</button>
    <router-view></router-view>
  </div>
</template>
<script>
import ProductInfo from "@/components/ProductInfo.vue";
import { Productlist } from "@/assets/products";
export default {
  components: { ProductInfo },
  data() {
    return {
      product: ""
    };
  },
  methods: {
    edit() {
      this.$router.push({ name: "Edit" });
    }
  },
  created: function() {
    this.product = Productlist.filter(
      data => data.id == this.$route.params.id
    )[0];
  }
};
</script>
<style scoped>
.list {
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
</style>
