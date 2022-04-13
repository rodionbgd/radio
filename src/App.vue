<script setup>
import RadioGroup from "@/components/RadioGroup.vue";
import RadioItem from "@/components/RadioItem.vue";

import { reactive } from "vue";

const dataPart = {
  disabled: false,
  title: "",
};
const data = reactive({
  status: {
    items: ["all", "upcoming", "ongoing", "complete"],
    ...dataPart,
  },
  color: {
    items: ["red", "green", "blue", "white"],
    ...dataPart,
  },
});

const toggleStatus = () => {
  data.status.disabled = !data.status.disabled;
  data.status.title = "";
};

const updateStatusTitle = (title) => {
  data.status.title = title;
};

const toggleColor = () => {
  data.color.disabled = !data.color.disabled;
  data.color.title = "";
};

const updateColorTitle = (title) => {
  data.color.title = title;
};
</script>

<template>
  <div class="h-screen flex flex-col items-center py-16 bg-gray-100">
    <RadioGroup @toggle-group="toggleStatus">
      <template #title>
        Status
        <span v-if="data.status.title"
          >: {{ data.status.title }}</span
        ></template
      >
      <template #main>
        <RadioItem
          v-for="item in data.status.items"
          :key="item"
          :item="item"
          :disabled="data.status.disabled"
          @update-radio="updateStatusTitle"
        />
      </template>
    </RadioGroup>

    <RadioGroup @toggle-group="toggleColor">
      <template #title>
        Status
        <span v-if="data.color.title && !data.color.disabled"
          >: {{ data.color.title }}</span
        ></template
      >
      <template #main>
        <RadioItem
          v-for="item in data.color.items"
          :key="item"
          :item="item"
          :disabled="data.color.disabled"
          @update-radio="updateColorTitle"
        />
      </template>
    </RadioGroup>
  </div>
</template>

<style></style>
