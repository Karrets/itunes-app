<script>
import ExplicitToggle from "@/components/ExplicitToggle.vue";

export default {
  name: "QueryBox",
  components: {ExplicitToggle},

  data() {
    return {
      search: {
        explicit: false
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
      <input class="form-control" type="search" placeholder="Search" aria-label="Search">
      <explicit-toggle v-model="search.explicit"></explicit-toggle>
      <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
  </div>
</template>

<style scoped>
#querybox {
  min-height: 50px;
}
</style>