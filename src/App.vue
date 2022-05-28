<script setup>
import { RouterLink, RouterView } from "vue-router";
import HelloWorld from "@/components/HelloWorld.vue";
import ItemList from "@/components/ItemList.vue";
import AddList from "@/components/AddList.vue";
</script>

<script>
export default {
  components: {
    ItemList,
    AddList
  },
  data() {
    return {
      item: [{ id: Date.now(), text: "Beli Baju", checked: true }]
    }
  },
  methods: {
    addList(event) {
      this.item.push({
        id: Date.now(),
        text: event,
        checked: false
      })
    },
    updateCheck(id, text, val) {
      console.log(val)
      this.item.forEach((item) => {
        if (item.id == id) {
          item.checked = val
        }
      })
    }
  }
}
</script>

<template>
  <h1>My Todoist </h1>
  <h5>Test Vue Composition API</h5>
  
  <ul>
    <ItemList v-for="row in item" :id="row.id" :checked="row.checked" :text="row.text" :key="row.id" @checklist="updateCheck" />
  </ul>
  <AddList @addlist="addList" />
</template>

<style>
h1 , h5{
  font-family: Arial, Helvetica, sans-serif;
  margin-top: 5px ;
  margin-bottom: 5px ;
  color: white;
}

body {
  margin: 0;
  padding: 0;
  background-color: rgb(54, 54, 54);
}

#app {
  border: 1px solid rgb(170, 170, 170);
  border-radius: 14px;
  padding: 20px;
  width: 40%;
  margin: 40px auto;
}

ul {
  margin-block-start: 0;
  margin-block-end: 0;
  margin-inline-start: 0;
  margin-inline-end: 0;
  padding-inline-start: 0;
}
</style>
