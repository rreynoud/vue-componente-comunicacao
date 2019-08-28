<template>
  <div class="row">

    <!-- coluna 1 -->
    <div class="col-8">

      <h2>Filmes</h2>

      <div class="list-group list-group-flush">

        <FilmesListaIten 
         v-for="filme in filmes" 
         :key="filme.id"
         :filme="filme"
         :class="aplicarClasseAtiva(filme)"
         @selecionarFilme="filmeSelecionado = $event"
         />

      </div>
    </div>

    <!-- coluna 2 -->
    <div class="col-4">

      <FilmesListaItenInfo 
      v-if="!editar"
      :filme="filmeSelecionado" 
      @editarFilme="editarFilme"
      />

      <FilmesListaItenEditar 
      v-if="editar"
      :filme="filmeSelecionado"       
      />


    </div>

  </div>
</template>

<script>

import { eventBus } from './../main'

import FilmesListaIten from './FilmesListaIten.vue'
import FilmesListaItenInfo from './FilmesListaItenInfo.vue'
import FilmesListaItenEditar from './FilmesListaItenEditar.vue'


export default {
  components: {
    FilmesListaIten,
    FilmesListaItenInfo,
    FilmesListaItenEditar
  },
  data(){
      return{
        filmes: [
          { id: 1, titulo: 'Vingadores: Guerra infinita ' , ano: 2019, diretor: "Stan Lee"},
          { id: 2, titulo: 'Homem formiga' , ano: 2019, diretor: "Stan Lee"},
          { id: 3, titulo: 'Pantera negra' , ano: 2019, diretor: "Stan Lee"}
        ],
        filmeSelecionado: undefined,
        editar: false
      }
  },
  methods:{
    aplicarClasseAtiva(filmeIterado){
      return{
        active : this.filmeSelecionado && this.filmeSelecionado.id === filmeIterado.id
      }
    },
    editarFilme(filme){
      this.editar = true
      this.filmeSelecionado = filme
    }
  }, created(){
    eventBus.$on('selecionarFilme', (filme)=>{
      this.filmeSelecionado = filme
    })
  }
}
</script>
