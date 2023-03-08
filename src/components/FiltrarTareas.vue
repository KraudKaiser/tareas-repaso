<template>
  <div>
	<label >Filtrar Tareas:</label>
	<input type="text" v-model="filtro">
  </div>
</template>

<script>
export default {
	props:{
		value:String
	},
	computed:{
		filtro:{
			get(){
				return this.value
			},
			set(val){
				this.$emit("input", val)
			}
		}
	}
}
</script>

<style>

</style>