<template>
  <div class="flex-d">
    <div class="input-group mb-3">
      <div class="input-group-prepend">
        <span class="input-group-text">
          Add Todo
        </span>
      </div>
      <input type="text" class="form-control" v-model="todoText" />
      <button class="btn btn-success" @click="$emit('addToDo', todoText)">
        Confirm
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return { todoText: "" };
  },
};
</script>
