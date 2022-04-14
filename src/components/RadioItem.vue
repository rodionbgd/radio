<template>
  <div class="filter-switch-item flex relative h-8 bg-gray-300x">
    <input
      type="radio"
      class="sr-only"
      :id="props.item"
      :name="props.name"
      :disabled="props.disabled"
      @change="updateValue"
    />
    <label
      class="h-8 py-1 px-2 text-sm leading-6 bg-white rounded shadow"
      :for="props.item"
      :class="{
        'text-gray-300': props.disabled,
        'opacity-80': props.disabled,
        'hover:text-gray-800': !props.disabled,
        'text-gray-600': !props.disabled,
      }"
    >
      {{ props.item }}
    </label>
  </div>
</template>

<script setup>
const props = defineProps({
  item: {
    type: String,
    required: true,
    default: "",
  },
  name: {
    type: String,
    required: false,
    default: "",
  },
  disabled: {
    type: Boolean,
    default: false,
  },
});

const events = defineEmits({
  "update-value": null,
});

const updateValue = () => {
  events("update-value", props.item);
};
</script>

<style scoped>
label {
  cursor: pointer;
}

input:checked + label {
  color: inherit;
}

input:not(:checked) + label {
  --bg-opacity: 0;
  box-shadow: none;
}
</style>
