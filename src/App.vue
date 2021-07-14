<template>
  <div class="container">
    <h2 class="title">Stocke app</h2>
    <Stocks />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Stocks from "./components/Stocks.vue";

export default defineComponent({
  name: "App",
  components: {
    Stocks
  }
});
</script>
