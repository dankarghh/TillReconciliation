<script setup>
const props = defineProps({
  modelValue: {
    type: Number,
  },
  type: {
    type: String,
  },
  label: {
    type: String,
  },
  name: {
    type: String,
  },
  step: {
    type: String,
  },
});

const emit = defineEmits(["update:modelValue"]);
</script>

<template>
  <div v-if="props.type == 'number'" class="">
    <label class="text-sm text-right">{{ label }}</label>
    <div class="relative">
      <p class="absolute left-2 top-1 text-gray-500">$</p>
      <input
        class="p-[5px] border mb-1 rounded-lg text-right shadow-sm"
        :value="modelValue"
        type="number"
        placeholder="0"
        :step="step"
        :name="name"
        @input="$emit('update:modelValue', $event.target.value)"
      />
    </div>
  </div>
  <div v-else>
    <label class="text-sm ml-1">{{ label }}</label>
    <div class="relative">
      <p class="absolute left-2 top-1 text-gray-500">$</p>
      <input
        class="p-[5px] border mb-1 rounded-lg text-right shadow-sm"
        :value="modelValue"
        type="number"
        placeholder="0"
        :name="name"
        @input="$emit('update:modelValue', $event.target.value)"
      />
    </div>
  </div>
</template>
