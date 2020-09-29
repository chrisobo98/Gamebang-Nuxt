<template>
  <div class="text-black antialiased">
    <navigation></navigation>
    <Nuxt />
  </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import axios from 'axios'

axios.defaults.headers.common['Client-ID'] = 'xhqybo0nhm7hscpd0oacjzs2rzb49r'
axios.defaults.headers.common['Authorization'] = 'Bearer j7or84o4mqqjwk514jhcw6ql18uuzi'
axios.defaults.headers.common['X-Requested-With'] = 'XMLHttpRequest'

export default {
  components: {
    Navigation
  }
}
</script>


