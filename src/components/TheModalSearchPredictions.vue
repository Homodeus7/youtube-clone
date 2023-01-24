<template>
  <BaseModal class="md:w-4/5 max-w-2xl">
    <p class="text-base text-black tracking-wide">Report search predictions</p>
    <TheSearchPredictionsList
      v-model="selectedSearchPredictions"
      :search-predictions="searchPredictions"
    />
    <template #footer="{ close }">
      <button
        @click="close"
        class="uppercase text-sm font-medium tracking-wider py-2.5 px-4 ml-auto mr-1 focus:ouline-none"
      >
        Cancel
      </button>
      <button
        class="uppercase text-sm font-medium tracking-wider py-2.5 px-4 ml-1 mr-1 focus:ouline-none text-gray-400 cursor-auto"
        disabled
      >
        Report
      </button>
    </template>
  </BaseModal>
</template>

<script>
import BaseModal from "./BaseModal.vue";
import TheSearchPredictionsList from "./TheSearchPredictionsList.vue";

export default {
  components: {
    BaseModal,
    TheSearchPredictionsList,
  },

  data() {
    return {
      selectedSearchPredictions: [],
      searchPredictions: [
        "new york giants",
        "new york alicia keys",
        "new york giants vs washington football",
        "new york",
        "new york song",
        "new york new york frank sinatra",
        "new york jets",
        "new york city",
        "new york giants live",
        "new york state of mind",
        "new york giants vs washington football live",
        "new york giants injury",
        "new york giants live stream",
        "new york accent",
      ],
    };
  },
};
</script>
