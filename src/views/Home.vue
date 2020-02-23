<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/Logo.png" />

    <Catalog msg="Maynard's Juggling Emporium" />
  </div>
</template>

<script>
// @ is an alias to /src

import Catalog from "@/views/Catalog.vue";

export default {
  name: "Home",
  components: {
    Catalog
  }
};
</script>
<style>
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
