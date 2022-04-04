<template>
<ul class="news__list">
    
    <div class="card-group justify-content-center">
        
     <div v-for="article in articles"  v-bind:key="article" class="news__item col-sm-3"  style="margin:10px;">
         
         <img class="card-img-top" :src="article.urlToImage" alt="" >
          <div class="card-body">
         <h6 class="card-title">{{article.title}}</h6>
         <p>{{article.description}}</p>

         </div>
         
     </div>    
     </div>    
     
     
    


     </ul>
</template>
<script>

export default {
    data() {
        return {
            articles:[]
        };
 },
 created() {
     let self=this;
     fetch('https://newsapi.org/v2/top-headlines?country=us',
     {
         headers: {
             Authorization: `Bearer ${import.meta.env.VITE_NEWSAPI_TOKEN}`
             }
             })
             .then(function(response) {
                 return response.json();
                 })
                 .then(function(data) {
                     console.log(data);
                     self.articles=data.articles;
                     
                     });
                      }
                      };

</script>
<style >
.card-img-top{
  height: 12rem;
  
}

.news__item{
  border-style: ridge;
  border-bottom-color: darkgreen;
  
}

</style>