<template>
    <div>
        <ul class="list-group">

            <todo-item 
                v-for="todo in todos" 
                :key="todo.id" 
                :todo="todo"
            />

            <todo-footer
                v-if="todos.length !== 0"
            />

            <li 
            v-if="todos.length === 0" 
            class="List-group-item text-center"
            > 
                Todas la tarea son completada
            </li>

            <todo-filtrer/>

        </ul>
        
    </div>
</template>
<script>
import { computed, inject, provide, ref } from 'vue'
import todoItem from './todoItem.vue'
import TodoFooter from './todoFooter.vue'
import TodoFiltrer from './todoFiltrer.vue'
export default {
  components: { todoItem, TodoFooter, TodoFiltrer },
    setup(){
        const todosTodo = inject('todos')
        const estado = ref('all')
        const todos = computed(()=>{

            if(estado.value === 'all'){
                return todosTodo.value
            } else if(estado.value === 'activos'){
                return todosTodo.value.filter(item => !item.estado)
            } else if(estado.value === 'completed'){
                return todosTodo.value.filter(item => item.estado)
            }
            
        })

        provide('estado',estado)
        return {todos}
    }
}
</script>
<style>
    
</style>