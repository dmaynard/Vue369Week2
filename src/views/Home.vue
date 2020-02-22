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
