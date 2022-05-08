<template>
  <main>
    <div class="container">
      <div class="wrapper d-flex wrap cg-2 rg-1" v-if="!loading">
        <MusicList :song="song"  v-for="(song, index) in filteredMusic" :key="index"/>
      </div>
      <!-- /.wrapper -->
      <div class="load" v-else>
          loading ...
      </div>
    </div>
    <!-- /.container -->
  </main>
</template>

<script>
import axios from "axios";
import state from '@/state.js';
import MusicList from "@/components/MusicListComponent";

export default {
  name: "SiteMain",
  components: {
    MusicList,
  },

  data() {
    return {
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      music: null,
      loading: null,
      error: null,
    };
  },

  methods: {
    callApi() {
      axios
        .get(this.API_URL)
        .then((response) => {
          this.music = response.data.response;
          this.loading = false;

        })
        .catch((error) => {
          console.error();
          error;
          this.error = `Sorry There is a problem! ${error}`;
        });
    },
  },

  computed: {
    filteredMusic() {
        return this.music.filter(song => {
          return song.genre.toLowerCase().includes(state.searchGenre.toLowerCase())
          // return song.title.toLowerCase().includes(state.searchText.toLowerCase());
        })
     
    }
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
        height: 260px;
        //   aspect-ratio: 1 / 1.2;
        margin: 0.75rem auto;
        background-color: $bg-nav;
        // border: 2px solid rgb(6, 231, 62);

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

    .load{
        height: 90%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        font-size: 28px;
        color: #1ed760;
    }
  }
}
</style>