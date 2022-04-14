<template>
  <div>
    <div class="block">
      <button
        class="text-gray-700 hover:rounded-lg px-1 hover:bg-sky-200 cursor-pointer"
        @click="toggleGroup"
      >
        Toggle
      </button>
      <span>{{ props.value }}</span>
    </div>
    <div
      class="filter-switch block inline-flex items-center relative h-10 p-1 space-x-1 bg-gray-200 rounded-md font-semibold text-blue-600 my-4"
    >
      <slot :disabled="props.disabled" :n="props.name" />
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  name: {
    type: String,
    required: true,
  },
  disabled: {
    type: Boolean,
    required: true,
  },
});
const events = defineEmits({
  "toggle-group": null,
});
const toggleGroup = () => {
  events("toggle-group");
};
</script>

<style scoped></style>
