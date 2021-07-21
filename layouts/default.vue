<template>
  <div class="text-black antialiased">
    <navigation></navigation>
    <Nuxt />
  </div>
</template>

<script>
import Navigation from "@/components/Navigation";
import axios from "axios";

axios.defaults.headers.common["Client-ID"] = "y55605g80xe9oogu0it9mla583bvez";
axios.defaults.headers.common["Authorization"] =
  "Bearer es0vv9ebcaykmrgrj1fr1a4unq2iyq";
axios.defaults.headers.common["X-Requested-With"] = "XMLHttpRequest";

export default {
  components: {
    Navigation
  }
};
</script>
