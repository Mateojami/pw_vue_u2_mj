<template>
  <div>
    <label for="id_nombre">Nombre</label>
    <input v-model="nombre" id="id_nombre" type="text" />
    <p>{{ nombre }}</p>

    <label for="id_apellido">Apellido</label>
    <input v-model="apellido" id="id_apellido" type="text" />

    <button v-on:click="imprimirNombre()">Imprimir Nombre</button>
    <button v-on:click="agregarEstudiante()">Agregar Estudiante</button>
    <h1>{{ arreglo[2] }}</h1>


    <hr />
    <label for="id_nombre_1">Nombre:</label>
    <input id="id_nombre_1" type="text">
    <label for="id_apellido_1">Apellido:</label>
    <input v-on:keypress.enter="agregarEstudiante1" id="id_apellido_1" type="text">

    <ul>
        <li 
        v-show="nombre" 
        v-for="{nombre, apellido} in arreglo" 
        :key="nombre"
        >
            {{nombre }} - {{apellido }}
        </li>
        
    </ul>
    
    <h2>Tabla</h2>
    <table border="2">
        <thead>
            <tr>
                <th>Nombre</th>
                <th>Apellido</th>
            </tr>
        </thead>
        <tbody>
            <tr 
            v-for="{nombre, apellido} in arreglo" 
            :key="nombre"
            >
                <td>{{ nombre }}</td>
                <td>{{ apellido }}</td>
            </tr>
        </tbody>
    </table>
  </div>
</template>

<script>
export default {
    data() {
        return {
            nombre: 'null',
            apellido: 'null',
            /*arreglo: [1, 2, 3, 4, 5],*/
            arreglo: [],
        };
    },

    methods: {
        imprimirNombre() {
            console.log(this.nombre);
        },
        agregarEstudiante() {
            const estu = {
                nombre: this.nombre,
                apellido: this.apellido,
            };
            console.log("Se agrega el estudiante:");
            console.log(estu);
            this.arreglo.push(estu);
            this.limpiarFormulario();
            
        
        },

        agregarEstudiante1(event) {
            console.log("Evento");
            if (event.charCode !== 13) {
                return;
            }
             const estu = {
                nombre: document.getElementById("id_nombre_1").value,
                apellido: document.getElementById("id_apellido_1").value,
            };
            console.log("Entro a agregar estudiante 1");
            console.log("Presiono el ENTER");
            console.log(estu);
            this.arreglo.push(estu);
            
            console.log(event);
            console.log(event.charCode);
            this.limpiarFormulario();
        },

        limpiarFormulario() {
            this.nombre = "";
            this.apellido = "";
        },  
        
    },

}
</script>

<style>
</style>