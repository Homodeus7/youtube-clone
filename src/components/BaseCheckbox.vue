<template>
  <input
    type="checkbox"
    class="h-5 w-5 cursor-pointer"
    :id="id"
    :value="value"
    v-model="selectedSearchPredictions"
  />
  <label :for="id" class="pl-4 cursor-pointer flex-grow">
    {{ value }}
  </label>
</template>

<script>
export default {
  props: {
    modelValue: Array,
    value: String,
    id: Number,
  },

  emits: ["update:modelValue"],

  data() {
    return {
      selectedSearchPredictions: this.modelValue,
    };
  },

  watch: {
    selectedSearchPredictions() {
      this.$emit("update:modelValue", this.selectedSearchPredictions);
    },
  },
};
</script>
