<template>
  <div>
      <ul v-for="item in sendList" :key="item.id">
          <li>{{item.title || item.name}}</li>
          <li>{{item.original_title || item.original_name}}</li>
          <li>
              <img v-if="showLang(item.original_language)" :src="flag(item.original_language)" :alt="item.original_language">
              <span v-else>{{item.original_language}}</span>
          </li>
          <li>{{item.vote_average}}</li>
      </ul>
  </div>
</template>

<script>
export default {
name: 'Card',
props:['sendList'],
methods: {
    flag(lang){
        if(lang == "en"){
            return require ("@/assets/images/en.png");
        } else if (lang == "it"){
            return require ("@/assets/images/it.png"); 
        }
    }, 
    showLang(lang){
        if(lang == "en" || lang == "it"){
            return true;
        }
    }
}
}
</script>

<style>

</style>