<template>
  <div>
    <h1>Maynard's Juggling Emporium</h1>
    <div id="example-3">
      <input type="checkbox" id="balls" value="Balls" v-model="categories" />
      <label class="lbl" for="balls">Balls</label>
      <input type="checkbox" id="clubs" value="Clubs" v-model="categories" />
      <label for="clubs" class="lbl">Clubs</label>
      <input type="checkbox" id="rings" value="Rings" v-model="categories" />
      <label for="rings" class="lbl">Rings</label>
    </div>
    <h3>Showing {{ categories }}</h3>
    <main>
      <div v-for="product in filteredProducts" :key="product.id">
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
import productlist from "@/assets/products.js";
export default {
  name: "Catalog",
  components: { ProductInfo },
  data() {
    return {
      productarray: productlist,
      balls: true,
      clubs: true,
      categories: ["Balls", "Clubs", "Rings"]
    };
  },
  created() {
    // this.products = ProductArray.ProductArray;
    console.log(this.productarray);
  },
  computed: {
    filteredProducts: {
      get() {
        return this.productarray.filter(prod => {
          let isOK = false;
          this.categories.forEach(cat => {
            if (prod.category === cat) isOK = true;
          });

          return isOK;
        });
      }
    }
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
.img {
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
.lbl {
  padding-right: 20px;
}
</style>
