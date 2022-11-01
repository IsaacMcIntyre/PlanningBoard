<script setup>
const todoItems = [
  {name: "Service boiler"}, {name: "Gas check"}, {name: "Wash dishes"}
]

</script>

<template>
  <h2><slot /></h2>
  <ul v-if="todoItems">
    <li v-for="item in todoItems">{{item.name}}<button>Delete</button></li>
  </ul>
</template>
