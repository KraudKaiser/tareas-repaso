<template>
  <div>
    <label> Nueva Tarea</label>
    <input type="text" v-model="tarea" @keyup.enter="agregarTarea">
    <button @click="agregarTarea">Agregar</button>
  </div>
</template>

<script>
export default {
    name:"TareaNueva",
    data(){
        return{
            tarea:""
        }
    },
    methods:{
        agregarTarea(){
            if(this.tarea.length > 0){
                this.$emit("nuevaTarea", this.tarea)
                this.tarea = ""
            }else{
                alert("La tarea esta vacia. Escriba algo")
            }
        }
    }
}
</script>

<style>

</style>