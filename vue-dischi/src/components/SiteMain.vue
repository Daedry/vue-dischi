<template>
  <main>
    <div class="container">
      <div class="wrapper d-flex wrap cg-2 rg-1">
        <div class="card col-2" v-for="(song, index) in music" :key="index">
          <!-- <div class="card col-2"> -->
          <div class="card-img">
            <img :src="song.poster" alt="" />
          </div>
          <div class="card-text">
            <h3>{{ song.title }}</h3>
            <p>{{ song.author }}</p>
            <p>{{ song.year }}</p>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
export default {
  name: "SiteMain",

  data() {
    return {
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      music: null,
    };
  },

  methods: {
    callApi() {
      axios.get(this.API_URL).then((response) => {
        this.music = response.data.response;
      });
    },
  },

  mounted() {
    this.callApi();
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/scss/style.scss";
main {
  .container {
    height: calc(100vh - 121px);
    background-color: $bg-main;

    .wrapper {
    //   border: 2px solid red;
      width: 1000px;
      height: 100%;
      margin: auto;

      .card {
        // width: 180px;
        height: 260px;
        //   aspect-ratio: 1 / 1.2;
        margin: 0.75rem auto;
        // border: 2px solid rgb(6, 231, 62);
        background-color: $bg-nav;

        .card-img {
          width: 80%;
          aspect-ratio: 1 / 1;
          margin: 1rem auto;
        //   border: 1px solid rgb(200, 146, 255);
          img {
            object-position: center;
            object-fit: contain;
          }
        }

        .card-text {
        //   width: 0%;
          aspect-ratio: 1 / 0.5;
          margin: 1rem auto;
        //   border: 1px solid rgb(194, 191, 33);
          text-align: center;

          h3 {
            color: $text-white;
            margin-bottom: 1rem;
            font-size: 16px;
          }

          p {
            color: $text-gray;
            font-size: 14px;

          }
        }
      }
    }
  }
}
</style>