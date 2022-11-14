<script setup lang="ts">
import { randomUUID } from 'crypto';
import { Ref, ref } from 'vue'
import { TodoItem } from './TodoList.vue';

interface Props {
  item: TodoItem
}

const defaultItem = { id: 'randomUUID()', name: 'wash dishes', deleted: false }

const props = withDefaults(defineProps<Props>(), {
  item: defaultItem
})



</script>

<template>
  {{ item.name }}
  <button v-if="!item.deleted" @click="$emit('delete', item.id)">Delete
    {{
    item.id
    }}</button>

  <!-- <button @click="increment">Count is: {{ count }}</button> -->
</template>
