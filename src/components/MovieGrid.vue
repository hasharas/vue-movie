<template>
  <section class="movie-grid">
    <div class="container">
      <!-- Top bar with title and search -->
      <div class="top-bar">
        <h2 class="title">Collect your favourites</h2>
        <div class="search-wrapper">
          <img :src="searchIcon" alt="Search" class="search-icon-left" />
          <input
            type="text"
            placeholder="Search title and add to grid"
            v-model="searchQuery"
            @input="searchMovies"
            class="search"
          />
        </div>
      </div>

      <hr class="hr" />

      <!-- Movies Grid -->
      <div class="movies">
        <div v-for="(movie, index) in movies" :key="index" class="movie-card">
          <button class="close" @click="removeMovie(index)">
            <span class="close-icon-bg">
              <img :src="closeIcon" alt="Close" />
            </span>
          </button>
          <img :src="movie.image?.medium || fallbackImage" alt="movie poster" />

<!--  <img :src="batMen" alt="Batman" v-if="movie.name === 'Batman'" />  -->

          <h3>{{ movie.name }}</h3>
          <p v-html="movie.summary || 'No description available.'"></p>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import searchIcon from "@/assets/Icons/Search White.svg";
import closeIcon from "@/assets/Icons/Close Grey.svg";
// import batMen from "@/assets/Images/Batman.jpg";

export default {
  data() {
    return {
      searchQuery: "",
      movies: [],
      fallbackImage: "https://via.placeholder.com/210x295?text=No+Image",
      searchIcon,
      closeIcon,
    };
  },
  mounted() {
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
  background-color: #191919ff;
  padding: 60px 20px;
  color: white;
}

.container {
  max-width: auto;
  margin: 0px;
  padding: 0 50px ;
}

.hr {
  border: none;
  height: 2px;
  background-color: #d3d3d3ff;
  margin: 20px 0;
}

.top-bar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 10px;
  gap: 20px;
}

.title {
  font-size: 25px;
  margin: 0;
  flex: 1;
  min-width: 200px;
  font-weight: 600;
}

/* Search input wrapper with icon on the left */
.search-wrapper {
  position: relative;
  width: 31%;
  max-width: 100%;
}

.search-wrapper input.search {
  padding: 10px 10px 10px 35px;
  font-size: 16px;
  width: 100%;
}

.search-icon-left {
  position: absolute;
  top: 50%;
  left: 10px;
  transform: translateY(-50%);
  width: 18px;
  height: 18px;
  pointer-events: none;
}

.search {
  background-color: #191919ff;
  color: white;
  border: 1px solid #dededeff;
  border-radius: 4px;
  width: 100%;
  padding: 10px;
  font-size: 12px;
  font-weight: 200;
}

/* Movies grid */
.movies {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 40px;
}

.movie-card {
  background: #262626ff;
  width: 31%;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: column;
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
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
}

/* Close icon  */
.close {
  position: absolute;
  top: 8px;
  right: 8px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
}

.close-icon-bg {
  background-color: #191919ff;
  padding: 15px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.close-icon-bg img {
  width: 12px;
  height: 12px;
}

/* Tablet */
@media screen and (max-width: 992px) {
  .movie-card {
    width: 47%;
  }

  .top-bar {
    flex-direction: column;
    align-items: stretch;
  }

  .search-wrapper {
    width: 100%;
  }
}

/* Mobile */
@media screen and (max-width: 600px) {
  .movie-card {
    width: 100%;
  }

  .movies {
    justify-content: center;
  }

  .title {
    text-align: center;
  }
}
</style>
