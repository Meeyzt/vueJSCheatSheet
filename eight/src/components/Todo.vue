<template>
  <div
    class="text-light bg-dark pa-2 flex d-flex justify-content-between border align-items-center px-1 py-2 rounded-lg shadow"
  >
    <span class="text">{{ todo.text }}</span>
    <button class="btn btn-danger" @click="$emit('deleteToDo', todo.id)">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  props: ["todo"],
};
</script>
