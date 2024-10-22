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

const removeTodo = (toDo) => {
    toDoArray.value = toDoArray.value.filter((t) => t !== toDo)
}
</script>

<template>
<h1 class="header">do IT!</h1>

<form @submit.prevent="addTodo">
    <input @submit.prevent="addTodo" v-model="doIt" class="element" placeholder="Was willste machen?" type="text">
    <br/>
    <br/>
    <button class="btn" value="doIt">click!</button>  ... oder drück' enter
    </form>
    <p class="elementSmall" placeholder="input">>>{{ doIt }}<<</p>
    <p class="elementSmall">{{ doIt.length }}/100</p>

<ul >
    <li v-for="(toDo, index) in toDoArray" class="list">
        {{ toDo.item }}
        <button @click="removeTodo(toDo)" value="toDo">X</button>
    </li>
</ul>
</template>

<style scoped>

</style>
