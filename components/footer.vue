<template>
  <v-footer dark padless>
    <v-card-text class="justify-center d-flex">
      <v-btn v-for="icon in icons" :key="icon" class="mx-4 white--text" icon>
        <v-icon size="24px">
          {{ icon }}
        </v-icon>
      </v-btn>
    </v-card-text>
    <v-row justify="center" no-gutters>
      <v-btn
        v-for="link in links"
        :key="link"
        color="white"
        text
        rounded
        class="my-2"
      >
        {{ link }}
      </v-btn>

      <v-card-text class="white--text justify-center d-flex">
        {{ new Date().getFullYear() }} GameHang —
        <strong class="ml-1"> Made with ❤️ in Central Florida</strong>
      </v-card-text>
    </v-row>
  </v-footer>
</template>
<script>
export default {
  data: () => ({
    icons: ["mdi-facebook", "mdi-twitter", "mdi-linkedin", "mdi-instagram"],
    links: ["Home", "About Us", "Team", "Services", "Blog", "Contact Us"]
  })
};
</script>
