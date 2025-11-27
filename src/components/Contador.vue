<template>
    <div>
        <h1>{{tit}}</h1>
        <p>{{numero}} <sup>2</sup>= {{calculaCuadrado}}</p>
        <p>{{numero}} <sup>2</sup>= {{calculaCuadrado}}</p>
        <p>{{numero}} <sup>2</sup>= {{calculaCuadrado}}</p>
        <p>{{numero}} <sup>2</sup>= {{calculaCuadrado}}</p>
        <p>{{numero}} <sup>2</sup>= {{calcularCubo}}</p>
        <p>{{numero}} <sup>2</sup>= {{obtenerCubo()}}</p>

        <div>
            <button v-on:click="incrementar">+</button>
            <button @:click="decrementar">-</button>
            <button v-show="mostrar">prueba</button>
        </div>

      
        
    </div>
  
</template>

<script>
import { computed } from 'vue';

 
export default {
    data() {
        return {
            numero: this.inicio,
            titulo: 'Contador',
            
        };
    },

    methods: {
        obtenerCuadrado() {
            console.log("Entro a obtenerCuadrado");
            return this.numero * this.numero;
        },
        obtenerCubo() {
            console.log("Entro a obtenerCubo");
            return this.numero * this.numero * this.numero;
        },
        incrementar() {
            console.log(this.tit);
            this.numero++;
        },
        decrementar() {
            this.numero--;
        },
    },
    computed: {
        calculaCuadrado() {
            console.log("Entro a propiedad computada");
            return this.numero * this.numero;
        },
        calcularCubo() {
            console.log("Entro a propiedad computada del cubo");
            return this.numero * this.numero * this.numero;
        },
    },
   /* props: ['tit', 'inicio', 'mostrar'], declaracion basica de props*/
   props: {
        tit: String,
        inicio: {
            type: Number,
            default: 99,
            validator(value) {
                return value > 10; /*mientras el valor de inicio sea mayor que 10 funciona */
            }
        },
        mostrar: Boolean
    }
    /*String, Number, Boolean, Array, Object, Date, Function, BigInt (todos los tipos de props)*/
    
};

</script>
<style> 

</style>
