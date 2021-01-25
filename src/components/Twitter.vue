<template>
  <div class="row"> 
    <div v-for="(art, index ) in info"  v-bind:key="index" class="col-sm-6">
      <div class="card" v-on:click="linkTo(art.url)" >
        <div class="card-head" >
          <img :src="(art.urlToImage)" class="card-img-top" :alt="art.title" :id="'card' + index">
        </div>
        <div class="card-body" >
          <h5 class="card-title">{{ art.title }}</h5>
          <h6 class="card-subtitle mb-2 text-muted">Source: {{ art.source.id }} {{ art.source.name }} {{ art.publishedAt }}</h6>
          <p class="card-text" style="max-height: 50px; overflow: hidden;">{{ art.description }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'Twitter',
  data: function () {
    return {
      info:"",
      imageSrc: [
        {
          src: '', 
          id: ''
          }
        ]
    }
  },
  mounted () {
    axios
      .get('http://newsapi.org/v2/top-headlines?' +
          'country=us&' +
          'apiKey=8f7f05239dc44c22be183428ebf1a9ff')
      .then(response => {
        this.info = response.data.articles,
          this.fillImgData()
         
    });
  },
   methods: {
     fillImgData() {
       var ref = this
         this.info.forEach(function callback(element, key) {
          ref.imageSrc.src = element.urlToImage
          ref.imageSrc.key = key
         ref.checkResource(element.urlToImage,key)
      });


      
     },
     checkResource (url, index) {
      var req = new XMLHttpRequest()
      req.open('HEAD', url, true)
      req.send()
      if (req.status === 404) {
        return index
      }
      if (req.status === 403) {
        return index
      }
   },
   linkTo(url) {
    window.location.href=url
    
   }
    }




}
</script>
