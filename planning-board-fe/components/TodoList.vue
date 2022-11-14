<script setup lang="ts">
import { randomUUID } from 'crypto';
import { type } from 'os';
import { Ref, ref } from 'vue'

export type TodoItem = {
  id: string
  name: string,
  deleted: boolean
}

const todoItems: Ref<TodoItem[]> = ref([
  { name: "Service boiler", deleted: false, id: randomUUID() }, { name: "Gas check", deleted: false, id: randomUUID() }, { name: "Wash dishes", deleted: false, id: randomUUID() }
])

function deleteTodoItem() {
  console.log('id')
  // todoItems.value.find(todoItem => todoItem.id === id).deleted = true
  // console.log(todoItems.value.find(todoItem => todoItem.id === id))
}
</script>

<template>
  <div v-if="todoItems">
    <TodoItem v-for="item in todoItems" :item="item" />
    <br />
    <br />
    <TodoItem />

  </div>
  <!-- <button @click="increment">Count is: {{ count }}</button> -->
</template>
