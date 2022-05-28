<template>
    <input type="text" v-model="newTodo"  placeholder="⚡️ Tugas baru..." @keyup.enter="createNewTodo" />
</template>

<script setup>
import { ref } from 'vue';
const newTodo = ref("");
const emit = defineEmits(['addlist']);
function createNewTodo(){
    let _newTodo = newTodo.value
    emit('addlist', _newTodo)
    newTodo.value = ""
}
</script>


<style scoped>
input {
    margin-top: 20px;
    margin-bottom: 5px;
    padding-top: 10px;
    padding-bottom: 10px;
    width: 100%;
    border-left: none;
    border-top: none;
    border-right: none;
    border-bottom: 1px solid rgb(255, 255, 255);
    font-size: 1.1rem;
    color:white;
    background-color: transparent;
}

input:focus {
    outline: none;
}
</style>