<script>
import ItemCard from "@/components/ItemCard.vue";
import QueryBox from "@/components/QueryBox.vue";

export default {
  name: "App",
  components: {QueryBox, ItemCard},

  data() {
    return {
      queryResults: []
    }
  },

  methods: {
    updateSearch(newSearch) {

    }
  }
}
</script>

<template>
  <query-box @update-search="updateSearch()"></query-box>
  <hr/>
  <item-card v-if="queryResults.length > 0" v-for="(item, i) in queryResults" :key="`item-card-${i}`" :item="item"></item-card>
  <div v-else class="m-auto"><h3>We couldn't find anything related to what you searched... 😢</h3></div>
</template>

<style scoped>

</style>
