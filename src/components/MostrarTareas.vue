<template>
  <div>
    <h2>Gestion de Tareas</h2>
	<notificar-tareas :notificar="notificar"></notificar-tareas>
	<span>Vigentes:{{ obtenerTareasVigentes }}</span> <span>Eliminadas: {{ tareasElimindas }}</span> <span>Totales: {{ obtenerTareasTotales }}</span>
    <tarea-nueva @nuevaTarea="agregarTarea"></tarea-nueva>
	<br>
	<filtrar-tareas v-model="filtro"></filtrar-tareas>
	<div v-if="cargando"> Cargando...</div>
		<lista-tarea v-else :tareas="obtenerTareasFiltradas" @eliminarTarea="removerTarea" @tarea-editada="editarTarea" ></lista-tarea>
	
  </div>
</template>

<script>
import ListaTarea from './ListaTarea.vue';
import TareaNueva from './TareaNueva.vue';
import FiltrarTareas from './FiltrarTareas.vue';
import NotificarTareas from './NotificarTareas.vue';
export default {
    name:"MostrarTareas",
    components:{
      TareaNueva,
        ListaTarea,
		FiltrarTareas,
		NotificarTareas
    },
	computed:{
		obtenerTareasFiltradas(){
			let reg = new RegExp(this.filtro, "i")
			return this.tareas.filter(tarea => reg.test(tarea))
		},
		obtenerTareasVigentes(){
			return this.tareas.length
		},
		obtenerTareasTotales(){
			return this.obtenerTareasVigentes + this.tareasElimindas
		}
	},
    data(){
        return{
            tareas:[],
			filtro:"",
			tareasElimindas:0,
			notificar:null,
			cargando:false
        }
    },
	watch:{
		notificar(){
			setTimeout(()=>   this.notificar = null, 1500)
		}

	},
	mounted(){
		this.cargando = true
		setTimeout(()=>{
			this.tareas = ["Aprender Vue", "Aprender Vuex", "Aprender Vuetify"]
			this.cargando = false
		}, 1500)
	},
    methods:{
      agregarTarea(tarea){
        this.tareas.push(tarea)
		this.setNotificar("agregar")
      },
	removerTarea(index){
		this.tareas.splice(index,1),
		this.tareasElimindas ++
		this.setNotificar("eliminar")
	},
	editarTarea(index, texto){
		this.$set(this.tareas, index, texto)
		this.setNotificar("editar")
	},
	setNotificar(val){
		this.notificar = val
	}
    },
}
</script>

<style scoped>

</style>