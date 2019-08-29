<template>
    <div>
        <h2>Editar filme</h2>

        <div class="form-group">
            <label>Título:</label>
            <input 
                type="text" 
                class="form-control" 
                placeholder="Insira o título"
                :value="filmeSelecionado.titulo"
                @input="filmeSelecionado = {propriedade: 'titulo', valor: $event.target.value }"
                >
        </div>
        
        <div class="form-group">
            <label>Título:</label>
            <input 
                type="text" 
                class="form-control" 
                placeholder="Insira o ano do filme"
                :value="filmeSelecionado.ano"
                @input="filmeSelecionado = {propriedade: 'ano', valor: $event.target.value }"
                >
        </div>

    </div>
</template>
<script>
export default {
    props :{
        filme: {
            type: Object,
            required: false
        }
    },
    data(){
        return{
            filmeLocal: this.filme
        }
    }
    ,computed:{
        filmeSelecionado: {
            get(dados){
                this.filmeLocal = Object.assign(
                    {},
                    this.filmeLocal,
                    {[dados.propriedade]:dados.valor}
                );
            },
            get(){
                return this.filme
            }
        }
    }
}
</script>
