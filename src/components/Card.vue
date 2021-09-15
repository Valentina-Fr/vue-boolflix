<template>
      <div class="card">
          <img class="img-fluid poster" :src="poster(item.poster_path)" :alt="item.original_title || item.original_name">
         <ul>
          <li class="none title">{{item.title || item.name}}</li>
          <li class="none w-25 py-1">
              <img class="img-fluid" v-if="showLang(item.original_language)" :src="flag(item.original_language)" :alt="item.original_language">
              <span v-else>{{item.original_language}}</span>
          </li>
          <li class="none original-title">{{item.original_title || item.original_name}}</li>
          <li class="none rating">
              <i v-for="number in 5" :key="number" 
              class="fa-star"
              :class="number <= rating? 'fas' : 'far'"></i>
          </li>
      </ul>
        </div>
</template>

<script>
export default {
name: 'Card',
props:['item'],
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
    },
    poster(img){
        const baseUri = "https://image.tmdb.org/t/p/w342";
        if(img == null) return "https://www.altavod.com/assets/images/poster-placeholder.png";
        return `${baseUri + img}`;
    },
},
computed: {
    rating(){
        return Math.ceil(this.item.vote_average / 2);
    },
}
}
</script>

<style scoped lang="scss">
    .none {
        display: none;
    }
    .card:hover {
        .poster {
            filter: grayscale(100%);
            opacity: 0.5;
        }
        .none {
            display: block;
        }
    }
    .card {
        position: relative;
        font-size: 0.8rem;
    }
    ul {
        position: absolute;
        padding: 8px;
    }
    .title, .original-title {
        font-weight: 700;
    }
</style>