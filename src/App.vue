<script>
import ItemCard from "@/components/ItemCard.vue";
import QueryBox from "@/components/QueryBox.vue";
import $ from 'jquery';

export default {
  name: "App",
  components: {QueryBox, ItemCard},

  data() {
    return {
      queryResults: null
    }
  },

  methods: {
    updateSearch(search) {
      console.log(search);

      $.get(
          'https://itunes.apple.com/search',
          {
            term: search.query,
            media: search.type,
            explicit: search.explicit,
            limit: 20,
          },
          (data) => {
            this.queryResults = data.results;
          },
          'json'
      );
    }
  }
}
</script>

<template>
  <div>
    <query-box @update-search="updateSearch"
               class="border-bottom border-2 border-secondary-subtle card-header"></query-box>
  </div>
  <div v-if="queryResults === null"></div>
  <div v-else-if="queryResults.length > 0" class="card-body overflow-scroll d-flex flex-column gap-3">
    <item-card v-for="(item, i) in queryResults" :key="`item-card-${i}`" :item="item"></item-card>
  </div>
  <div v-else class="m-auto card-body">
    <h3 class="m-auto">We couldn't find anything related to what you searched... 😢</h3>
  </div>
</template>

<style scoped>
</style>
