<template>
  <div class="container mx-auto py-16">
    <h1 class="font-heading uppercase mb-8">The Most Hyped Up Games Ever</h1>
    <div class="game-container flex flex-wrap -mx-4">
      <nuxt-link :to="'/games/' + game.id" v-for="game in games" :key="game.id" class="w-full md:w-1/5 px-4 mb-12 no-underline">
        <img :src="game.cover.url.replace('t_thumb', 't_cover_big')" alt="cover">
        <div class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots">{{ game.name }}</div>
        <div class="text-grey-darker text-base overflow-hidden whitespace-no-wrap overflow-dots pb-1">{{ game.genres[0].name }}</div>
      </nuxt-link>
    </div>
  </div>
</template>

</template>

<script>
import axios from 'axios'

export default {
  components : {
    
  },
  asyncData({ params, error }) {
    return axios
      .get(`https://api.igdb.com/v4/games/?fields=name,genres.name,cover.url,hypes&order=hypes`)
      .then(res => {
        return { 
          games: res.data 
          }
      })
      .catch(e => {
        console.log(e)
      })
  },
  data() {
    return {
      games: []
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
</style>
