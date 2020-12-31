<template>
    <div>
        <li class="list-group-item list-group-item-dark d-flex justify-content-between align-items-center">
            <span 
                role='buttom' 
                :class="{'completed':todo.estado}"
                @click="completado(todo.id)"
            >
                {{todo.text}}
            </span>
            <span role="button">
                <i class="fas  fa-times" @click="eliminar(todo.id)"></i>
            </span>
        </li>
    </div>
</template>
<script>

import { inject } from 'vue'
export default {

    props:{
        todo: {
            type: Object,
            required: true
        }
    },

    setup(){

        const todos = inject('todos')

        const eliminar = id =>{
            todos.value = todos.value.filter(item => item.id !== id)
        }

        const completado = id =>{
            todos.value = todos.value.map(item => {
               
                if(item.id === id){
                    item.estado=true;
                } 
                return item
            })
            
        }

        return {eliminar, completado}
    }
    
}
</script>

<style>
    .completed{
        text-decoration: line-through;
    }
</style>