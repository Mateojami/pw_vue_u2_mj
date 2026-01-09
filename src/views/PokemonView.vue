<template>
    <div>
        <PokemonImagen v-if="pokemonGanador" :pokemonId="pokemonGanador.id" />
        <PokemonOpciones @seleccionado="evaluarGanador($event)" :listaPokemons="pokemonArr" />
        
        <div v-if="mostrarResultado">
            <h1>{{ esGanador ? 'Ganador' : 'Perdedor' }}</h1>
        </div>

    </div>
</template>

<script>
import PokemonImagen from '../components/PokemonImagen.vue';
import PokemonOpciones from '../components/PokemonOpciones.vue';   
import { obtenerPokemonFachada, obtenerAleatorioFachada } from '../clients/PokemonClient.js';
export default {
    components: {
        PokemonImagen,
        PokemonOpciones
    },
    data() {
        return {
            pokemonArr: [],
            pokemonGanador: null,
            mostrarResultado: false,
            esGanador: false
            
        };
    },
    mounted() {
        console.log('Componente montado');
        this.iniciarJuego();
    },
    methods: {
        async iniciarJuego(){
            this.pokemonArr = await obtenerPokemonFachada();

            const idAleatorio = obtenerAleatorioFachada(0,3);
            this.pokemonGanador = this.pokemonArr[idAleatorio];


        },
        evaluarGanador(idGanador){
            this.mostrarResultado = true;
            this.esGanador = idGanador === this.pokemonGanador.id;
        },
    }
}
</script>

<style>
div h1 {
    text-align: center;
    font-size: 48px;
    margin-top: 30px;
    padding: 20px;
    background-color: yellow;
    border: 3px solid black;
    color: black;
}
</style>