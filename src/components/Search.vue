<template>
  <div class="input-group w-25">
    <input type="text" class="form-control" @keyup.enter="$emit('research', searchTerm)" v-model="searchTerm" :placeholder="placeholder">
    <div class="input-group-append">
      <button class="btn btn-danger" type="button" @click="$emit('research', searchTerm)">Cerca</button>
    </div>
  </div>
</template>

<script>

export default {
    name: 'Search',
    props: ["placeholder"],
    data(){
      return {
        searchTerm:"",
      }
    },
}
</script>

<style>

</style>