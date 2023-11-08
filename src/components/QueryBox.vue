<script>
export default {
  name: "QueryBox",

  emits: ['update-search']
}
</script>

<template>
  <div id="querybox" class="d-flex align-content-center">

    <form class="d-flex" role="search">
      <input class="form-control me-2" type="search" placeholder="Search" aria-label="Search">
      <button class="btn btn-outline-success" type="submit">Search</button>
    </form>
    
  </div>
</template>

<style scoped>
#querybox {
  min-height: 50px;
}
</style>