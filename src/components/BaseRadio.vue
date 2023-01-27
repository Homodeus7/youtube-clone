<template>
  <input
    type="radio"
    class="h-5 w-5 cursor-pointer"
    :id="id"
    v-model="selectedSearchPredictionCategory"
  />
  <label v-if="$slots.default" :for="id" class="pl-4 cursor-pointer flex-grow">
    <slot />
  </label>
</template>

<script>
export default {
  props: {
    id: String,
    modelValue: String,
  },
  emits: ["update:modelValue"],

  data() {
    return {
      selectedSearchPredictionCategory: this.modelValue,
    };
  },

  watch: {
    selectedSearchPredictionCategory() {
      this.$emit("update:modelValue", this.selectedSearchPredictionCategory);
    },
  },
};
</script>
