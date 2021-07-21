<template>
  <div>
    <div
      class="bg-indigo-900"
      :style="`background:url(${backgroundImage}); background-size: cover; `"
    >
      <div
        class="container mx-auto flex flex-col md:flex-row items-end pb-8 p-6"
        style="height:300px"
      ></div>
    </div>

    <div class="container mx-auto flex flex-col md:flex-row p-6">
      <div class="w-full md:w-1/4 -mt-16">
        <img
          :src="game.cover.url.replace('t_thumb', 't_cover_big')"
          alt="cover"
          class="mb-8"
        />
        <div class="mb-4 text-white">
          <span class="font-semibold">Platforms:</span>
          <span v-for="platform in game.platforms" :key="platform.id"
            >{{ platform.name }},
          </span>
        </div>

        <div class="mb-4 text-white">
          <span class="font-semibold ">Released:</span>
          <span>{{ new Date(game.first_release_date).toDateString() }}</span>
        </div>

        <div class="mb-10 text-white" v-if="game.total_rating">
          <div class="text-5xl font-semibold">
            {{ Math.round(game.total_rating) }}%
          </div>
          <div class="font-semibold">Overall Rating</div>
        </div>
      </div>

      <div class="w-full md:w-3/4 md:ml-12 py-8 leading-normal">
        <div class="w-full md:w-1/4"></div>
        <div class="w-full md:w-3/4">
          <h1
            class="font-black text-5xl font-heading font-sans text-lg text-white mb-4"
          >
            {{ game.name }}
          </h1>
        </div>
        <p class="mb-12 text-white">{{ game.summary }}</p>

        <div class="flex flex-wrap -mx-4">
          <a
            href="#"
            v-for="screenshot in game.screenshots"
            :key="screenshot.cloudinary_id"
            class="w-full md:w-1/4 px-4 mb-12 no-underline"
          >
            <img
              :src="screenshot.url.replace('t_thumb', 't_screenshot_med')"
              alt="screenshot"
            />
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  computed: {
    getOfficialWebsite() {
      return this.game.websites.filter(website => website.category === 1)[0]
        .url;
    },
    backgroundImage() {
      function getRandomInt(max) {
        return Math.floor(Math.random() * max);
      }
      return this.game.screenshots[getRandomInt(5)].url.replace(
        "t_thumb",
        "t_1080p"
      );
    }
  },
  asyncData({ params, error }) {
    const proxyurl = "https://blooming-taiga-18504.herokuapp.com/";

    return axios
      .get(
        `${proxyurl}https://api.igdb.com/v4/games/${params.id}/?fields=name,cover.url,summary,platforms.name,first_release_date,websites,total_rating,screenshots.url,total_rating,platforms,screenshots,cover`
      )
      .then(res => {
        return {
          game: res.data[0]
        };
      })
      .catch(e => {
        console.log(e);
      });
  },
  head() {
    return {
      title: this.game.name + " | GameBang"
    };
  }
};
</script>
