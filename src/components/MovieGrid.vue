<template>
  <section class="movie-grid">
    <div class="container">
      <h2 class="title">Collect your favourites</h2>
      <input
        type="text"
        placeholder="Search title and add to grid"
        v-model="searchQuery"
        @input="searchMovies"
        class="search"
      />

      <div class="movies">
        <div v-for="(movie, index) in movies" :key="index" class="movie-card">
          <button class="close" @click="removeMovie(index)">✖</button>
          <img :src="movie.image?.medium || fallbackImage" alt="movie poster" />
          <h3>{{ movie.name }}</h3>
          <p v-html="movie.summary || 'No description available.'"></p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      searchQuery: "",
      movies: [],
      fallbackImage: "https://via.placeholder.com/210x295?text=No+Image",
    };
  },
  mounted() {
    // Optional: load 3 initial movies
    this.initialMovies(["batman", "spiderman", "wild"]);
  },
  methods: {
    async initialMovies(queries) {
      for (let q of queries) {
        const res = await fetch(`https://api.tvmaze.com/search/shows?q=${q}`);
        const data = await res.json();
        if (data.length) this.movies.push(data[0].show);
      }
    },
    async searchMovies() {
      if (this.searchQuery.trim() === "") return;

      const res = await fetch(
        `https://api.tvmaze.com/search/shows?q=${this.searchQuery}`
      );

      const data = await res.json();
      if (data.length) {
        const newMovie = data[0].show;
        // Avoid duplicates (by ID)
        if (!this.movies.find((m) => m.id === newMovie.id)) {
          this.movies.push(newMovie);
        }
      }
    },
    removeMovie(index) {
      this.movies.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.movie-grid {
  background: #fff;
  padding: 60px 20px;
  background-color: #242424ff;
}

.title {
  font-size: 30px;
  text-align: center;
  margin-bottom: 20px;
}

.search {
  display: block;
  margin: 0 auto 40px auto;
  padding: 10px;
  width: 300px;
  font-size: 16px;
}

.movies {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 30px;
}

.movie-card {
  background: #474747ff;
  width: 250px;
  position: relative;
}

.movie-card img {
  width: 100%;
  height: auto;
}

.movie-card h3 {
  margin: 10px 0 5px;
  font-size: 18px;
  padding: 0 15px;
}

.movie-card p {
  font-size: 14px;
  color: #ccc;
  padding: 0 15px;
  margin-bottom: 15px;
  display: -webkit-box;
  -webkit-line-clamp: 3; /* Limit to 3 lines */
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

.close {
  position: absolute;
  top: 8px;
  right: 8px;
  border: none;
  background: transparent;
  font-size: 18px;
  cursor: pointer;
  color: red;
}

/* Responsive */
@media screen and (max-width: 768px) {
  .movies {
    flex-direction: column;
    align-items: center;
  }
}
</style>
