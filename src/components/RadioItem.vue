<template>
  <div class="filter-switch-item flex relative h-8 bg-gray-300x">
    <input
      type="radio"
      :id="props.item"
      class="sr-only"
      name="status"
      :value="props.item"
      v-model="checked"
      @input="check"
    />
    <label
      :for="props.item"
      class="h-8 py-1 px-2 text-sm leading-6 bg-white rounded shadow"
      :class="{
        'text-gray-300': props.disabled,
        'hover:text-gray-800': !props.disabled,
        'text-gray-600': !props.disabled,
      }"
    >
      {{ props.item }}
    </label>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";

const props = defineProps({
  item: {
    type: String,
    required: true,
    default: "",
  },
  disabled: {
    type: Boolean,
    required: true,
    default: false,
  },
});

const events = defineEmits({
  "update-radio": null,
});
const checked = ref("");
const check = (event) => {
  if (props.disabled) {
    setTimeout(() => {
      event.target.checked = false;
      events("update-radio");
    }, 0);
    return;
  }
  events("update-radio", event.target.value);
  checked.value = event.target.value;
};

watch(
  () => props.disabled,
  () => {
    if (props.disabled) {
      checked.value = "";
    }
  }
);
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
