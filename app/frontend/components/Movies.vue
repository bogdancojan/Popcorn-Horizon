<template>
  <div
    class="row row-cols-1 row-cols-md-3 g-4"
    :key="movie.id"
    v-for="movie in this.movies"
  >
    <MovieCard :movie="movie" />
  </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";

export default {
  data() {
    return {
      movies: [],
    };
  },
  methods: {
    async fetchMovies() {
      const res = await fetch("/apis/v1/movies");
      const data = await res.json();
      return data;
    },
  },
  async created() {
    this.movies = await this.fetchMovies();
  },
  components: {
    MovieCard,
  },
};
</script>
