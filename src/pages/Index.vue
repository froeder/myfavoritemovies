<template>
  <q-page>
    <div class="row q-pa-lg q-gutter-md flex flex-center">
      <div class="col-3" v-for="m in movies" v-bind:key="m.id">
        <q-card>
          <q-img
            src="https://cdn.quasar.dev/img/parallax2.jpg"
            basic
          >
            <div class="absolute-bottom text-h6">
              {{m.title}}
            </div>
          </q-img>

          <q-card-section>
            {{m.overview}}
          </q-card-section>
          <q-card-section>
            {{m.vote_average}}
          </q-card-section>
        </q-card>
      </div>
    </div>
  </q-page>
</template>

<script>
import Axios from 'axios'
export default {
  name: 'HomeScreen',
  data() {
    return {
      movies: new Object() 
    }
  } ,
  methods : {

  } , 
  mounted(){
    let self = this
    Axios.get("https://api.themoviedb.org/3/list/137674?api_key=446f26dec5122c9a80566828521adc36&language=pt-BR")
    .then(response => {
      self.movies = response.data.items
    })
  }
}
</script>
