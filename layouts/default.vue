<template>
  <v-app>
    <div class="text-black antialiased">
      <navbar></navbar>
      <Nuxt />
      <Footer></Footer>
    </div>
  </v-app>
</template>

<script>
import Navbar from "@/components/navbar.vue";
import Footer from "@/components/footer.vue";
import axios from "axios";

axios.defaults.headers.common["Client-ID"] = "y55605g80xe9oogu0it9mla583bvez";
axios.defaults.headers.common["Authorization"] =
  "Bearer es0vv9ebcaykmrgrj1fr1a4unq2iyq";
axios.defaults.headers.common["X-Requested-With"] = "XMLHttpRequest";

export default {
  components: {
    Navbar,
    Footer
  }
};
</script>
