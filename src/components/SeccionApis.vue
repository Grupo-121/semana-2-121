<template>
  <div class="d-inline-flex p-2 bd-highlight">
    <div class="row mt-md-5 mt-sm-5 mt-xs-5">
      <!--<p class="section-text">Section 2</p>-->
      <div
        class="col-lg-6 col-xs-12"
        v-for="(info, index) of info"
        :key="index"
      >
        <div class="d-flex justify-content-center align-items-center">
          <div class="p-3">
            <img :src="info.urlToImage" alt="movie poster" width="180" height="180"/>
          </div>
          <div class="p-2">
            <h5 class="text-primary">{{ info.title }}</h5>
            <hr />
            <p class="news-info" style="margin: 5; padding: 5">
              {{ info.description }}
              <!--{{ info.content }}-->
            </p>
            <p>Autor: {{ info.author }}</p>
          </div>
        </div>
        <div class="d-flex container-fluid justify-content-end pb-2 mt-n2">
          <a
            :href="info.url"
            class="btn btn-outline-info"
            >Leer mas</a
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'



export default {
    name: 'SeccionApis',
    data(){
        return{
            info: null
        }
    },
    mounted(){
        axios.get('http://newsapi.org/v2/top-headlines?country=co&category=science&apiKey=95e95d4de9f642c09f2234e110c08ac9')
        .then(response => {
            (this.info = response.data.articles.slice(0,4)) 
            console.log(this.info)
            })
    }
}

</script>
