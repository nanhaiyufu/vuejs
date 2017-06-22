<template>
  <div class="newslist">
    <div class="container">
      <ul class="media-list">
        <li class="media" v-for="article in articles">
          <div class="media-left">
            <a v-bind:href="article.url" target="_blank">
              <img calss="media-object" v-bind:src="article.urlToImage">
            </a>
          </div>

          <div class="media-body">
            <h4 class="media-heading">
              <a v-bind:href="article.url" target="_blank">{{ article.title }}</a>
            </h4>
              <h5><i>by: {{ article.author }} </i></h5>
              <p>{{article.description }} </p>

          </div>
        </li>
      </ul>
    </div>

  </div>
</template>
<script>
  export default{
    name: 'newslist',
    props: ['src'],
    methods:{
        updateNews(source){
            this.$http.get('https://newsapi.org/v1/articles?source=' + source + '&apiKey=249342508d2e4053986d75c9cf4a32a6')
              .then(response=>{
                  this.articles= response.data.articles;
              })
        }
    },

    data() {
        return {
          articles: []
        }
    },

    created: function() {
        this.updateNews(this.src);
    },

    watch: {
      src: function (val) {
        this.updateNews(val);
      }
    }
  }

</script>

<style>

</style>
