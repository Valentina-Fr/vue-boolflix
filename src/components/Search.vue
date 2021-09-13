<template>
  <div>
      <input type="text" v-model="searchTerm">
      <button type="button" @click="$emit('research', searchTerm)">Cerca</button>
  </div>
</template>

<script>

export default {
    name: 'Search',
    data(){
      return {
        searchTerm:"",
      }
    },
}
</script>

<style>

</style>