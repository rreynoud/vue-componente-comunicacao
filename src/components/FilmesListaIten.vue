<template>
    <li class="list-group-item">
        <span>{{filmeTitulo}} | {{filmeAno}} </span>
        <button class="btn btn-success float-right">Editar</button>
    </li>
</template>


<script>
export default {
    props: {
        filmeTitulo: {
            type: String,
            required: true
        },
        filmeAno:{
            type: Number,
            required: true
        }
    }
    ,
    created(){
        console.log('Filme titulo', this.filmeTitulo)
    }
}
</script>