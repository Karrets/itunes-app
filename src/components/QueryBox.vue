<script>
import ExplicitToggle from "@/components/ExplicitToggle.vue";

export default {
  name: "QueryBox",
  components: {ExplicitToggle},

  data() {
    return {
      search: {
        query: '',
        explicit: false,
        type: 'all'
      }
    }
  },

  emits: ['update-search']
}
</script>

<template>
  <div id="querybox" class="py-1">
    <div class="d-flex flex-row align-content-center pt-2">
      <h1 class="m-auto">iTunes Search</h1>
    </div>
    <form @submit.prevent="$emit('update-search', search)" id="querybox" class="py-3 d-flex flex-row align-content-center flex-grow-1 w-75 mx-auto gap-2" role="search">
      <input v-model="search.query" class="form-control" type="search" placeholder="Search" aria-label="Search">
      <div class="input-group w-50">
        <span class="input-group-text">Type: </span>
        <select v-model="search.type" class="form-select form-control">
          <option selected value="all">All</option>
          <option value="movie">Movie</option>
          <option value="podcast">Podcast</option>
          <option value="music">Music</option>
          <option value="musicVideo">Music Video</option>
          <option value="audiobook">Audiobook</option>
          <option value="shortFilm">Short Film</option>
          <option value="tvShow">TV Show</option>
          <option value="software">Software</option>
          <option value="ebook">E-Book</option>
        </select>
      </div>
      <explicit-toggle v-model="search.explicit"></explicit-toggle>
      <button class="btn btn-primary" type="submit">Search</button>
    </form>
  </div>
</template>

<style scoped>
#querybox {
  min-height: 50px;
}
</style>