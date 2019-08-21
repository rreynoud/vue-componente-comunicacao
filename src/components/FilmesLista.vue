<template>
  <div class="row">

    <!-- coluna 1 -->
    <div class="col-8">

      <h2>Filmes</h2>

      <div class="list-group list-group-flush">

        <FilmesListaIten 
         v-for="filme in filmes" 
         :key="filme.id"
         :filmeTitulo="filme.titulo"
         :filmeAno="filme.ano"/>

      </div>
    </div>

    <!-- coluna 2 -->
    <div class="col-4">

      <FilmesListaItenInfo/>

    </div>

  </div>
</template>

<script>

import FilmesListaIten from './FilmesListaIten.vue'
import FilmesListaItenInfo from './FilmesListaItenInfo.vue'

export default {
  components: {
    FilmesListaIten,
    FilmesListaItenInfo
  },
  data(){
      return{
        filmes: [
          { id: 1, titulo: 'Vingadores: Guerra infinita ' , ano: 2019},
          { id: 2, titulo: 'Homem formiga' , ano: 2019},
          { id: 3, titulo: 'Pantera negra' , ano: 2019}
        ]
      }
  }
}
</script>
