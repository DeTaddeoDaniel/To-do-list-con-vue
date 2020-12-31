<template>
    <div>

        <form  @submit.prevent="formulario">

            <input 
                type="text"
                class="form-control my-3 bg-dark text-white"
                placeholder="Ingrese tarea"
                v-model.trim="text"
            >
        </form>

    </div>
</template>

<script>
import { inject, ref } from 'vue'
    export default {
        setup(){
            // riceve valore variabile dal componente padre
            const todos = inject('todos')
            const text = ref('')
            
            const formulario = () => {

                console.log(text.value)

                if(text.value !== ''){

                    const todo={
                        text : text.value,
                        estado : false,
                        id : Date.now()
                    }

                    text.value = ''
                    todos.value.push(todo)
  
            
                } else {
                    console.log('Esta vacio')
                }  
            }

            // todo che uso en el template debe ser retornado
            return {formulario,text}
        }   
    }
</script>

<style>

</style>