<template>
  <div class="home">
    <div class="feature-card">
      <router-link to="/moviedetail/tt0988824">
        <img
          class="featured-img"
          src="../assets/narutoship.jpg"
          alt="Naruto: Shippûden"
        />
        <div class="detail">
          <h3>Naruto: Shippûden</h3>
          <button class="movie-type">Series</button>
        </div>
      </router-link>
    </div>

    <main>
      <div class="search-bar">
        <p>SEARCH</p>
        <form @submit.prevent="searchMovie()" class="search-box">
          <input v-model="searchInput" type="text" placeholder="Search...." />
          <button type="submit">
            <i class="fa fa-solid fa-magnifying-glass"></i>
          </button>
        </form>
      </div>

      <Loader v-if="loading" />
      <Poster v-if="poster" />
      <div class="movies-list">
        <div class="movie" v-for="movie in movies" :key="movie.imdbID">
          <router-link
            :to="'/moviedetail/' + movie.imdbID"
            class="movie-container"
          >
            <div class="cover-img">
              <img :src="movie.Poster" :alt="movie.Title" />
              <div class="movie-type">{{ movie.Type }}</div>
            </div>
            <div class="movie-detail">
              <p class="year">{{ movie.Year }}</p>
              <h3>{{ movie.Title }}</h3>
            </div>
          </router-link>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import key from "@/key";
import Loader from "../components/Loader.vue";
import Poster from "../components/Poster.vue";

export default {
  name: "HomeView",
  components: { Loader, Poster },
  data() {
    return {
      searchInput: "",
      movies: [],
      loading: false,
      poster: true
    };
  },
  methods: {
    searchMovie() {
      this.loading = true;
      this.poster = false;
      if (this.searchInput != "") {
        fetch(
          `https://www.omdbapi.com/?apikey=${key.apiKey}&s=${this.searchInput}`
        )
          .then((res) => res.json())
          .then((data) => {
            this.movies = data.Search;
            this.searchInput = "";
            this.loading = false;
            console.log(this.movies);
          })
          .catch((err) => console.log(err.message));
      }
    },
  },
};
</script>

<style>
.home {
  max-width: 1200px;
  margin: 10px auto;
  padding: 0 5px;
}
.home .feature-card {
  position: relative;
}
.home .featured-img {
  display: block;
  width: 100%;
  height: 450px;
  object-fit: cover;
  object-position: top;

  position: relative;
  z-index: 0;
}
.home .detail {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  padding: 25px;
  z-index: 1;
}
.home .detail h3 {
  color: white;
  font-size: 20px;
  font-weight: 600;
  margin-bottom: 20px;
}
.home .detail .movie-type {
  background: #111;
  color: #fff;
  padding: 10px 20px;
  outline: none;
  border: 0;
  border-radius: 5px;
}

.home main {
  /* background: grey; */
}
.home main .search-bar {
  background: #0e0d0df1;
  padding: 10px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.home main .search-bar .search-box {
  display: flex;
  align-items: center;
}
.home main .search-bar .search-box input {
  width: 0;
  border: none;
  outline: none;
  background: #222;
  transition: all 0.2s ease;
  width: 200px;
  padding: 10px;
  border-radius: 10px;
}
.home main .search-bar .search-box input:focus {
  background: #fff;
  width: 300px;
}
.home main .search-bar .search-box input::placeholder {
  font-size: 16px;
  font-weight: 400;
}
.home main .search-bar .search-box button {
  background: none;
  outline: none;
  border: none;
}
.home main .search-bar .search-box .fa {
  margin-left: 5px;
  cursor: pointer;
  background: #222;
  /* background: crimson; */
  padding: 10px;
  font-size: 16px;
  border-radius: 50%;
}

.movies-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 200px));
  padding: 20px;
  grid-gap: 20px;
}
.movies-list .movie {
  padding: 5px 10px;
}
.movies-list .movie .movie-container {
  display: flex;
  flex-direction: column;
  height: 100%;
}
.movies-list .movie .movie-container .cover-img {
  position: relative;
  display: block;
}
.movies-list .movie .movie-container .cover-img img {
  display: block;
  height: 280px;
  width: 100%;
  object-fit: cover;
}
.movies-list .movie .movie-container .cover-img .movie-type {
  background: #111;
  color: #fff;
  padding: 8px 16px;
  bottom: 16px;
  left: 0px;
  text-transform: capitalize;
}
.movies-list .movie .movie-container .movie-detail {
  padding: 15px 5px;
}
.movies-list .movie .movie-container .movie-detail .year {
  color: #aaa;
  font-size: 14px;
}
.movies-list .movie .movie-container .movie-detail h3 {
  color: #fff;
  font-weight: 600;
  font-size: 18px;
}
/* Media Queries */
@media screen and (max-width: 600px) {
  .movies-list {
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  }
  .home .featured-img {
    height: 330px;
  }
}

@media screen and (max-width: 450px) {
  .home main .search-bar .search-box input:focus {
    background: #fff;
    width: 205px;
  }
}
</style>
