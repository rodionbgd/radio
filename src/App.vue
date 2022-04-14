<script setup>
import RadioGroup from "@/components/RadioGroup.vue";
import RadioItem from "@/components/RadioItem.vue";

import { reactive } from "vue";

const dataPart = {
  disabled: false,
  title: "",
  value: "",
};
const data = reactive({
  status: {
    items: ["all", "upcoming", "ongoing", "complete"],
    name: "status",
    ...dataPart,
  },
  color: {
    items: ["red", "green", "blue", "white"],
    name: "color",
    ...dataPart,
  },
});

const toggleStatus = () => {
  data.status.disabled = !data.status.disabled;
};
const toggleColor = () => {
  data.color.disabled = !data.color.disabled;
};
const updateStatusValue = (value) => {
  data.status.value = value;
};
const updateColorValue = (value) => {
  data.color.value = value;
};
</script>

<template>
  <div class="h-screen flex flex-col items-center py-16 bg-gray-100">
    <RadioGroup
      :value="data.status.value"
      v-model="data.status.value"
      :disabled="data.status.disabled"
      :name="data.status.name"
      @toggle-group="toggleStatus"
    >
      <template v-slot:default="{ n, disabled }">
        <RadioItem
          v-for="(item, index) in data.status.items"
          :key="index"
          :item="item"
          @update-value="updateStatusValue"
          :disabled="disabled"
          :name="n"
        />
      </template>
    </RadioGroup>
    <RadioGroup
      :value="data.color.value"
      v-model="data.color.value"
      :name="data.color.name"
      :disabled="data.color.disabled"
      @toggle-group="toggleColor"
    >
      <template v-slot:default="{ n, disabled }">
        <RadioItem
          v-for="(item, index) in data.color.items"
          :key="index"
          :item="item"
          @update-value="updateColorValue"
          :disabled="disabled"
          :name="n"
        />
      </template>
    </RadioGroup>
  </div>
</template>

<style></style>
