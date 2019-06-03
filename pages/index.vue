<template>
  <section>
    <header class="hero-image">
      <div class="hero-text">
        <h1>Merlin Movie House</h1>
      </div>
    </header>
    <main>
      <h2>A Cinematic Experience</h2>
      <p>Merlin Movie House is a place where all your film dreams come true. Ride a dragon, fight a jedi, kiss a toad...</p>
      <hr />
      <h2>Now Playing</h2>
      <div class="card" style="width: 18rem;">
        <img class="card-img-top" alt="Card image cap">
        <div class="card-body">
          <h5 class="card-title">Card title</h5>
          <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
          <a href="#" class="btn btn-primary">Go somewhere</a>
        </div>
      </div>
    </main>
  </section>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      loading: true,
      movies: null,
      errored: false
    };
  },
  mounted () {
    axios.get('http://www.omdbapi.com/?t=her&apikey=29917929')
    .then(response => (this.movies = response.data))
    .catch(error => {
      console.log(error)
      this.errored = true
    })
    .finally(() => this.loading = false)
  }
}
</script>

<style>
/* Styling for main hero image */
.hero-image {
  background-image: url('../assets/header.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  background-position: bottom;
  position: relative;
  height: 600px;
  width: 100%;
}

/* Text laying over hero image */
.hero-text {
    text-align: center;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
}
header h1 {
  font-family: Limelight, sans-serif;
  font-size: 5em;
  font-weight: bold;
  text-transform: uppercase;
  text-shadow: 2px 2px black;
}

main {
  margin: 2rem 3rem;
  font-family: Merriweather;
}

nav {
  font-family: Merriweather;
}

</style>
