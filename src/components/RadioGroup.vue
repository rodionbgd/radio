<template>
  <div>
    <button
      class="text-gray-700 block hover:rounded-lg px-1 hover:bg-sky-200 cursor-pointer"
      @click="toggleGroup"
    >
      <slot name="title" />
    </button>
    <div
      class="filter-switch inline-flex items-center relative h-10 p-1 space-x-1 bg-gray-200 rounded-md font-semibold text-blue-600 my-4"
    >
      <slot name="main" />
    </div>
  </div>
</template>

<script setup>
const events = defineEmits({
  "toggle-group": null,
});
const toggleGroup = () => {
  events("toggle-group");
};
</script>

<style scoped></style>
