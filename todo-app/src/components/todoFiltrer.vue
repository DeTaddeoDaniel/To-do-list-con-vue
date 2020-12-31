<template>
    <div class="card mt-3">
        <div class="card-body list-group-item list-group-item-dark d-flex justify-content-around align-items-center">
            <span role="button" @click="filtrar('activos')">Activos</span>
            <span role="button" @click="filtrar('all')">Todos</span>
            <span role="button" @click="filtrar('completed')">Completed</span>
        </div>
    </div>
</template>

<script>
import { inject } from 'vue'
export default {
    setup(){
        const estado = inject('estado')

        const filtrar = valor =>{
            estado.value = valor
        }

        return {filtrar}
    }
    
}
</script>

<style>
    
</style>