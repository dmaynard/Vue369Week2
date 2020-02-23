<template>
  <div>
    <h1>Maynard's Juggling Emporium</h1>
    <div id="example-3">
      <span>
        <input
          type="checkbox"
          class="myCheckbox"
          id="balls"
          value="Show Juggling Balls"
          v-model="balls"
        />
        <label for="balls ">Show Juggling Balls</label>
        <p></p>
        <input
          type="checkbox"
          class="myCheckbox"
          id="clubs"
          value="Show Juggling Clubs"
          v-model="clubs"
        />
        <label for="clubs">Show Juggling Clubs</label>
      </span>
    </div>
    <main>
      <div v-for="product in productarray" :key="product.id">
        <ProductInfo :product="product">
          <template v-slot:title>
            <router-link
              class="link"
              tag="h1"
              :to="{ name: 'Id', params: { id: product.id } }"
              >{{ product.title }}</router-link
            >
          </template>
        </ProductInfo>
      </div>
    </main>
  </div>
</template>

<script>
import ProductInfo from "@/components/ProductInfo.vue";
import productarray from "@/assets/products.js";
export default {
  name: "Catalog",
  components: { ProductInfo },
  data() {
    return {
      productarray: productarray,
      balls: true,
      clubs: true,
      checkedNames: []
    };
  },
  created() {
    // this.products = ProductArray.ProductArray;
    // console.log(this.productarray);
  }
};
</script>

<style scoped>
.items {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
.link:hover {
  text-decoration: underline;
  color: blue;
  cursor: pointer;
}
.images {
  max-width: 40%;
  justify-content: center;
}
figure {
  display: flex;

  flex-direction: column;
}
.list {
  /* border: 1px solid black; */
  margin: 10px auto;
  box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
}
.extra {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
