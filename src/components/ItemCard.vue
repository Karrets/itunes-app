<script>
export default {
  name: "ItemCard",

  props: {
    item: Object
  }
}
</script>

<template>
  <div class="bg-primary-subtle card">
    <div class="row g-0 d-flex flex-row">
      <div class="col-md-auto">
        <img class="img-fluid rounded-start" :src="item.artworkUrl100" :alt="item.collectionName">
      </div>

      <div class="col-md-auto">
        <div class="card-body">
          <h5 class="card-title">{{item.collectionName}}</h5>
          <p class="card-text" v-html="item.description"></p>
          <p class="card-text" v-html="item.trackName"></p>
        </div>
      </div>
      <div class="col-md-auto m-auto me-3">
        <button @click="console.log(item)" class="btn btn-outline-secondary">Log JSON Object</button>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>