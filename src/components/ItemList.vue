<template>
    <li>
        <span v-bind:class="done ? 'done' : ''">{{ text }}</span>
        <button @click="updateList" v-bind:class="done ? 'done': ''">
            <span v-text="done ? 'Undo' : 'Done' "></span>
        </button>
    </li>
</template>

<script setup>
import { ref } from 'vue';

const props = defineProps({
    id: {
        type: Number,
        required: true
    },
    text: {
        type: String,
        required: false,
    },
    checked: {
        type: Boolean,
        required: false
    }
})

const emit = defineEmits(['checklist']);

const done = ref(props.checked)
const id = ref(props.id)
const text = ref(props.text)

function updateList(){
    done.value = !done.value;
    emit('checklist', id, text, done)
}

</script>

<style scoped>
span {
    font-family: Arial, Helvetica, sans-serif;
    color: white;
}
li {
    padding-top: 20px;
    padding-bottom: 5px;
    border-bottom: 1px solid rgb(206, 206, 206);
    color: rgb(204, 204, 204);
    list-style: none;
    display: flex;
}

button {
    margin-left: auto;
    font-weight: bold;
    cursor: pointer;
    background-color: #00FFAB;
    border-radius: 4px;
    padding: 4px;
    color: black;
    border: 2px solid transparent;
}
 button > span {
     color: black;
 }
button:hover{
    background-color: #14C38E;
    color:black;
}
button:active {
    border: 2px solid black;
}
.done {
  text-decoration: line-through;
  color: #999;
}

button.done{
    text-decoration: none;
    background-color: #ddd;
    color: rgb(3, 3, 3);
}
button.done::before{
    content: "✅ ";
}


</style>
