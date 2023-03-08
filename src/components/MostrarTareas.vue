<template>
  <div>
    <h2>Gestion de Tareas</h2>
    <tarea-nueva @nuevaTarea="agregarTarea"></tarea-nueva>
      <lista-tarea :tareas="tareas"></lista-tarea>
  </div>
</template>

<script>
import ListaTarea from './ListaTarea.vue';
import TareaNueva from './TareaNueva.vue';
export default {
    name:"MostrarTareas",
    components:{
      TareaNueva,
        ListaTarea
    },
    data(){
        return{
            tareas:["Aprender Vue", "Aprender Vuex", "Aprender Vuetify"]
        }
    },
    methods:{
      agregarTarea(tarea){
        this.tareas.push(tarea)
      }
    },
}
</script>

<style scoped>

</style>