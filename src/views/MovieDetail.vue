<template>
  <div class="movie-detail">
    <div class="title">
      <h3>{{movie.Title}}</h3>
      <ul>
        <li>{{movie.Year}}</li>
        <li>{{movie.Rated}}</li>
        <li>{{movie.Runtime}}</li>
      </ul>
    </div>
    <main>
      <div class="poster">
        <img :src="movie.Poster" :alt="movie.Title">
      </div>
      <div class="synopsis">

        <span>Series Info:</span>

        <ul>
          <li>
            <strong>Title:</strong>
            {{movie.Title}}
          </li>
          <li>
            <strong>Type:</strong>
            {{movie.Type}}
          </li>
          <li>
            <strong>Release Date:</strong>
            {{movie.Released}}
          </li>
          <li>
            <strong>Language:</strong>
            {{movie.Language}}
          </li>
          <li>
            <strong>Country:</strong>
            {{movie.Country}}
          </li>
          <li>
            <strong>Director:</strong>
            {{movie.Director}}
          </li>
        </ul>
      </div>
    </main>


    <div class="extra-info">
      <section>
        <div class="storyline">
          <h3>Storyline:</h3>
          <p>
            {{movie.Plot}}
          </p>
        </div>


        <div class="extra">
          <p>
            <strong>Genre:</strong>
            {{movie.Genre}}
          </p>
        </div>
        <div class="extra">
          <p>
            <strong>Stars:</strong>
            {{movie.Actors}}
          </p>
        </div>
        <div class="extra">
          <p>
            <strong>Writer: </strong>
            {{movie.Writer}}
          </p>
        </div>
        <div class="extra">
          <p>
            <strong>Awards: </strong>
            {{movie.Awards}}
          </p>
        </div>
      </section>
      <aside>
        <p>
          <strong>IMDb Rating:</strong>
          {{movie.imdbRating}}
        </p>
        <p>
          <strong>Metascore:</strong>
          {{movie.Metascore}}
        </p>
        <p>
          <strong>Production:</strong>
          {{movie.Production}}
        </p>
        <p>
          <strong>Rating:</strong>
          {{movie.Rated}}
        </p>
        <p>
          <strong>DVD:</strong>
          {{movie.DVD}}
        </p>
        <p>
          <strong>BoxOffice:</strong>
          {{movie.BoxOffice}}
        </p>
      </aside>
    </div>
    

  </div>
</template>

<script>
import key from '@/key.js'

// Vue.use(VueRouter)
export default {
  data () {
    return{
      id: this.$route.params.id,
      movie: [],
    }
  },
  beforeMount() {
    fetch(`https://www.omdbapi.com/?apikey=${key.apiKey}&i=${this.id}&plot=full`)
    .then(res => res.json())
    .then(data => {
      this.movie = data
      console.log(data)
    })
  }
}
</script>

<style>
  .movie-detail {
    max-width: 1200px;
    margin: 10px auto;
    padding: 5px 15px;
  }
  .movie-detail .title {
    padding: 5px;
    margin-bottom: 15px;
  }
  .movie-detail .title h3 {
    display: block;
    font-size: 35px;
    margin-bottom: 10px;
  }
  .movie-detail .title ul {
    display: flex;
    align-items: center;
  }
  .movie-detail .title li {
    display: inline-block;
    margin-right: 10px;
  }
  .movie-detail main {
    display: flex;
  }
  .movie-detail main .poster {
    max-width: 300px;
  }
  .movie-detail main .poster img {
    display: block;
    width: 100%;
    height: 350px;
    object-fit: cover;
  }
  .movie-detail main .synopsis {
    /* background: purple; */
    margin-left: 25px;
    
    margin-top: 30px;
    padding: 15px 5px;
  }
  .movie-detail main .synopsis span {
    display: block;
    font-size: 20px;
    font-weight: 400;
    margin-bottom: 10px;
  }
  .movie-detail main .synopsis ul {
    list-style: none;
  }
  .movie-detail main .synopsis ul li {
    line-height: 27px;
    font-size: 16px;
    font-weight: 400;
    text-transform: capitalize;
  }
  .movie-detail main .synopsis ul li strong {
    color: #707070;
    font-weight: 700;
  }
  .movie-detail .extra-info {
    display: flex;
    flex-wrap: wrap;
    margin-top: 25px;
  }
  .movie-detail .extra-info section {
    flex: 0 0 70%;
    max-width: 70%;
    padding: 10px;
  }
  .movie-detail .extra-info aside {
    flex: 0 0 30%;
    max-width: 30%;
    min-height: 30px;
    margin-top: 60px;
    padding: 10px;
  }
  .movie-detail .extra-info section .storyline {
    margin-bottom: 35px;
  }
  .movie-detail .extra-info section .storyline h3 {
    font-size: 20px;
    margin-bottom: 10px;
  }
  .movie-detail .extra-info section .storyline p {
    font-size: 16px;
    font-weight: 400;
  }
  .movie-detail .extra-info section .extra {
    padding: 15px 0;
    border-top: 1px solid #707070;
  }
  .movie-detail .extra-info section .extra:last-child {
    border-bottom: 1px solid #707070;
  }
  .movie-detail .extra-info section .extra p strong {
    font-weight: 500;
    font-size: 16px;
  }
  .movie-detail .extra-info aside p {
    line-height: 30px;
  }
  .movie-detail .extra-info aside p strong {
    font-weight: 500;
    font-size: 16px;
  }

  /* Media Queries */
  @media screen and (max-width: 780px) {
    .movie-detail .extra-info section {
      flex: 0 0 100%;
      max-width: 100%;
      padding: 10px;
    }
    .movie-detail .extra-info aside {
      flex: 0 0 100%;
      max-width: 100%;
      background: #111;
      display: flex;
      flex-wrap: wrap;
    }
    .movie-detail .extra-info aside p {
      line-height: 30px;
      margin-right: 15px;
    }
  }
  @media screen and (max-width: 600px) {
    .movie-detail main {
      display: block;
    }
  }
</style>
