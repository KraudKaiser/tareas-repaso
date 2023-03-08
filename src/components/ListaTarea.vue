<template>
  <ul>
    <li :key="index" v-for="(tarea, index) in tareas" >
        {{ tarea }}
    <button @click="">Eliminar</button>
    </li>
</ul>
</template>

<script>
export default {
    name:"ListaTarea",
    props:{
        tareas:[]
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