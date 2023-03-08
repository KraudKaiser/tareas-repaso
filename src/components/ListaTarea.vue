<template>
  <ul>
    <li :key="index" v-for="(tarea, index) in tareas" >
		<template v-if="editando === index">
			<input type="text" v-model="texto">
			<button @click="emitirTareaEditada">Confirmar</button>
		</template>
		<template v-else>
			{{ tarea }}
			<button @click="editarTarea(index, tarea)">Editar</button>
			<button class="eliminar" @click="eliminarTarea(index)" >Eliminar</button>
		</template>
    </li>
</ul>
</template>

<script>
export default {
    name:"ListaTarea",
    props:{
        tareas:[]
    },
	methods:{
		eliminarTarea(index){
			this.$emit("eliminarTarea", index)
		},
		editarTarea(index, tarea){
			this.editando = index
			this.texto = tarea
		},
		emitirTareaEditada(){
			this.$emit("tarea-editada", this.editando, this.texto)
			this.editando = null
			this.texto = ""
		}
	},
	data(){
		return{
			editando:null,
			texto:""
		}
	}
}
</script>

<style scoped>
    .eliminar{
        border: none;
        background-color: transparent;
        color:red
    }
</style>