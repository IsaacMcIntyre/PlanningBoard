<script setup lang="ts">
import { randomUUID } from 'crypto';
import { Ref, ref } from 'vue'

interface TodoItem {
  id: string
  name: string,
  deleted: boolean
}

const todoItems: Ref<TodoItem[]> = ref([
  { name: "Service boiler", deleted: false, id: randomUUID() }, { name: "Gas check", deleted: false, id: randomUUID() }, { name: "Wash dishes", deleted: false, id: randomUUID() }
])

function deleteTodoItem(id) {
  alert(id)
  todoItems.value.find(todoItem => todoItem.id === id).deleted = true
  console.log(todoItems.value.find(todoItem => todoItem.id === id))
}

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

</script>

<template>
  <h2>
    <slot />
  </h2>
  <ul v-if="todoItems">
    <li v-for="item in todoItems">{{ item.name }}<button v-if="!item.deleted" @click="deleteTodoItem(item.id)">Delete {{
        item.id
    }}</button></li>
  </ul>
  <button @click="increment">{{ count }}</button>
</template>
