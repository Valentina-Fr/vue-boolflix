<template>
  <section :id="id">
    <h2 class="text-white p-3">{{title}}</h2>
    <div class="container">
        <div class="row gy-3">
            <div class="col-sm-3" v-for="item in list" :key="item.id">
                <Card :item="item"/>
            </div>
        </div>
    </div>
  </section>
</template>

<script>
import Card from '@/components/Card.vue';
export default {
    name: "Section",
    components: {
        Card,
    },
    props: ["list", "id", "title"],
}
</script>

<style>

</style>