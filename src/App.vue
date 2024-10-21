<script setup>
import { ref } from 'vue'

const doIt = ref('')
const toDoArray = ref([
    {id: 1, item: 'Tu dies'}, 
    {id: 2, item: 'Tu das'},
    {id: 3, item: 'Tu jenes'},
])
    
const addTodo = () => {
    toDoArray.value.push({ id: toDoArray.value.length+1, item: doIt.value})
    doIt.value = ''
}
</script>

<template>
<h1 class="header">Todo!</h1>

<form @submit.prevent="addTodo">
    <input @submit.prevent="addTodo" v-model="doIt" class="element" placeholder="Was willste machen?" type="text">
    <br/>
    <br/>
    <button class="btn" value="doIt">Halt's fest</button>
    </form>
    <p class="element">{{ doIt }}</p>

<ul >
    <li v-for="toDo in toDoArray" class="list">
        {{ toDo.id }}
        {{ toDo.item }}
    </li>
</ul>
</template>

<style scoped>

</style>
