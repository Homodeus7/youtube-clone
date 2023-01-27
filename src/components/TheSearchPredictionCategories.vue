<template>
  <div class="space-y-3 text-black text-sm mt-5">
    <div
      v-for="(label, index) in categories"
      :key="label"
      class="flex items-center"
    >
      <BaseRadio
        :id="`search-prediction-category-${index}`"
        :value="label"
        v-model="selectedSearchPredictionCategory"
      >
        {{ label }}
      </BaseRadio>
    </div>
  </div>
</template>

<script>
import BaseRadio from "./BaseRadio.vue";

export default {
  components: {
    BaseRadio,
  },

  props: {
    categories: Array,
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
