<script setup>
import { ref } from 'vue'

const header = ref('doIt!')
const doIt = ref('')
const toDoArray = ref([
    {id: 1, item: 'Tu dies', did: false}, 
    {id: 2, item: 'Tu das', did: false},
    {id: 3, item: 'Tu jenes', did: true},
])
    
const addTodo = () => {
    toDoArray.value.push({ id: toDoArray.value.length+1, item: doIt.value})
    doIt.value = ''
}

const removeTodo = (toDo) => {
    toDoArray.value = toDoArray.value.filter((t) => t !== toDo)
}

const didThis = (toDo) => {
    console.log(toDo.did)
    toDo.did = !toDo.did
}
</script>

<template>
<h1 class="header">{{ header }}</h1>
<p v-if="doIt" class="element">🙂</p>
<p v-else class="element">🤔</p>
<form @submit.prevent="addTodo">
    <input @submit.prevent="addTodo" v-model="doIt" class="element" placeholder=" 🤔 Was willste machen?" type="text">
    <br/>
    <br/>
    <button class="btn" value="doIt">click!</button>  ... oder drück' enter
    </form>
    <p class="elementSmall" placeholder="input">>>{{ doIt }}<<</p>
    <p class="elementSmall">{{ doIt.length }}/100</p>

<ul >
    <li v-for="(toDo, did, index) in toDoArray" class="list" :class="{done: toDo.did}">
        <input type="checkbox" @click="didThis(toDo)" value="toDo">
        {{ toDo.item }}
        <button @click="removeTodo(toDo)" value="toDo">X</button>
    </li>
</ul>
</template>

<style scoped>

</style>
