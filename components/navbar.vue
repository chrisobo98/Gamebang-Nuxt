<template>
  <div class="bg-indigo-900 font-semibold">
    <div class="container mx-auto flex justify-between items-center py-6 p-6">
      <nuxt-link to="/" class="text-white no-underline hover:text-grey-light"
        >Home</nuxt-link
      >
      <div class="flex">
        <nuxt-link
          to="/"
          class="text-white no-underline hover:text-grey-light ml-6"
          >Blog</nuxt-link
        >
        <nuxt-link
          to="/about"
          class="text-white no-underline hover:text-grey-light ml-6"
          >About</nuxt-link
        >
        <nuxt-link
          to="/"
          class="text-white no-underline hover:text-grey-light ml-6"
          >Login</nuxt-link
        >
      </div>
    </div>
  </div>
</template>
