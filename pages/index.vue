<template>
  <div>
    <div
      class="py-20 bg-cover bg-no-repeat bg-fixed"
      style="background-image: url(https://media.vanityfair.com/photos/5ce426151c0b0773cacd1121/master/pass/star-wars-feature-vf-2019-summer-embed-05.jpg)"
    >
      <div class="container m-auto text-center px-6 opacity-100">
        <h2 class="text-4xl font-bold mb-2 text-white">
          GameHang, where gamer's come to, <br />
          well you know... hang out.
        </h2>
        <h3 class="text-2xl mb-8 text-gray-200">
          Are you ready to jump right into the action?
        </h3>
        <div class="relative p-2 w-full sm:max-w-2xl sm:mx-auto">
          <div class="overflow-hidden z-0 rounded-full relative p-3">
            <form role="form" class="relative flex z-50 bg-white rounded-full">
              <input
                type="text"
                placeholder="search for game"
                class="rounded-full flex-1 px-6 py-4 text-gray-700 focus:outline-none"
              />
              <button
                class="bg-purple-900 text-white rounded-full font-semibold px-8 py-4 hover:bg-purple-400 focus:bg-purple-600 focus:outline-none"
              >
                Search
              </button>
            </form>
            <div class="glow glow-1 z-10 bg-pink-400 absolute"></div>
            <div class="glow glow-2 z-20 bg-purple-400 absolute"></div>
            <div class="glow glow-3 z-30 bg-yellow-400 absolute"></div>
            <div class="glow glow-4 z-40 bg-blue-400 absolute"></div>
          </div>
        </div>
      </div>
    </div>

    <div class="container mx-auto py-16 p-6">
      <h1
        class="font-heading uppercase font-black text-4xl text-center font-heading font-sans text-white"
      >
        The Most Hyped Up Games Ever
      </h1>
      <h1
        class="font-heading text-2xl text-center font-heading font-sans mb-12 text-white"
      >
        Using Twitch's IGDB API, we're pulling up the games that had the most
        levels of hype
      </h1>
      <div class="game-container flex flex-wrap -mx-4">
        <nuxt-link
          :to="'/games/' + game.id"
          v-for="game in games"
          :key="game.id"
          class="w-full md:w-1/5 px-4 mb-12 no-underline"
        >
          <img
            :src="game.cover.url.replace('t_thumb', 't_cover_big')"
            alt="cover"
          />
          <div
            class="text-black font-semibold text-lg overflow-hidden whitespace-no-wrap overflow-dots text-white"
          >
            {{ game.name }}
          </div>
          <div
            class="text-grey-darker text-base overflow-hidden whitespace-no-wrap overflow-dots pb-1 text-white"
          >
            {{ game.genres[0].name }}
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import "../assets/main.css";

export default {
  components: {},
  data() {
    return {
      games: []
    };
  },
  async mounted() {
    await this.getHypeGames();
  },
  methods: {
    async getHypeGames() {
      const proxyurl = "https://blooming-taiga-18504.herokuapp.com/";
      const options = {
        method: "POST",
        url: `${proxyurl}https://api.igdb.com/v4/games/`,
        headers: {
          Accept: "application/json",
          "Client-ID": "y55605g80xe9oogu0it9mla583bvez",
          Authorization: `Bearer es0vv9ebcaykmrgrj1fr1a4unq2iyq`
        },
        data:
          "fields summary, cover.url, cover.image_id, genres.name, name, total_rating; where platforms =(6, 48, 49, 130); sort hypes asc; limit 20;"
      };
      await axios
        .request(options)
        .then(res => {
          this.games = res.data;
        })
        .catch(e => {
          console.log(e);
        });
    }
  }
};
</script>

<style>
.glow {
  top: -10%;
  left: -10%;
  width: 120%;
  height: 120%;
  border-radius: 100%;
}

.glow-1 {
  animation: glow1 4s linear infinite;
}

.glow-2 {
  animation: glow2 4s linear infinite;
  animation-delay: 100ms;
}

.glow-3 {
  animation: glow3 4s linear infinite;
  animation-delay: 200ms;
}

.glow-4 {
  animation: glow4 4s linear infinite;
  animation-delay: 300ms;
}

@keyframes glow1 {
  0% {
    transform: translate(10%, 10%) scale(1);
  }
  25% {
    transform: translate(-10%, 10%) scale(1);
  }
  50% {
    transform: translate(-10%, -10%) scale(1);
  }
  75% {
    transform: translate(10%, -10%) scale(1);
  }
  100% {
    transform: translate(10%, 10%) scale(1);
  }
}

@keyframes glow2 {
  0% {
    transform: translate(-10%, -10%) scale(1);
  }
  25% {
    transform: translate(10%, -10%) scale(1);
  }
  50% {
    transform: translate(10%, 10%) scale(1);
  }
  75% {
    transform: translate(-10%, 10%) scale(1);
  }
  100% {
    transform: translate(-10%, -10%) scale(1);
  }
}

@keyframes glow3 {
  0% {
    transform: translate(-10%, 10%) scale(1);
  }
  25% {
    transform: translate(-10%, -10%) scale(1);
  }
  50% {
    transform: translate(10%, -10%) scale(1);
  }
  75% {
    transform: translate(10%, 10%) scale(1);
  }
  100% {
    transform: translate(-10%, 10%) scale(1);
  }
}

@keyframes glow4 {
  0% {
    transform: translate(10%, -10%) scale(1);
  }
  25% {
    transform: translate(10%, 10%) scale(1);
  }
  50% {
    transform: translate(-10%, 10%) scale(1);
  }
  75% {
    transform: translate(-10%, -10%) scale(1);
  }
  100% {
    transform: translate(10%, -10%) scale(1);
  }
}
</style>
