<template>
    <todo-form/>
    <todo-list/>
</template>

<script>
import { provide, ref, watchEffect } from 'vue'
import todoForm from './todoForm.vue'
import TodoList from './todoList.vue'
export default {
    components: { todoForm, TodoList },
    setup(){
        
        // oggetto dinamico
        const todos = ref([])

        //passa todos al formulario (solo componenti figli)
        provide('todos',todos)

        if(localStorage.getItem('todos')){
            todos.value = JSON.parse(localStorage.getItem('todos'))
        }

        // osserva se cambia una proprietà che usa
        watchEffect(() =>{
            localStorage.setItem('todos',JSON.stringify(todos.value))
        })

    }
}
</script>

<style>
    
</style>