<template>
    <div>
        <li class="list-group-item list-group-item-primary d-flex justify-content-between align-items-center">
            
            <span> {{contarActivo}} activos
            </span>
            
            <span role="button" @click='vaciarCompletados'>
                Nascondi completado
            </span>

        </li>
    </div>
</template>
<script>
import { computed, inject } from 'vue'
export default {

    setup(){
        const todos = inject('todos')

        const contarActivo = computed(() =>{
            return todos.value.filter(item => !item.estado).length
        })

        const estado = inject('estado')    

        const vaciarCompletados = () => {
           estado.value = 'activos'
        }

        return {contarActivo, vaciarCompletados}
    }
    
}
</script>
<style>
    
</style>
// video 1.33.30