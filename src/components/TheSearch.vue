<template>
  <div class="flex w-full mr-2">
    <div class="relative w-full">
      <TheSearchInput />
      <TheSearchResult :results="keywords" />
    </div>
    <TheSearchButton />
  </div>
</template>

<script>
import TheSearchInput from "./TheSearchInput.vue";
import TheSearchButton from "./TheSearchButton.vue";
import TheSearchResult from "./TheSearchResult.vue";

export default {
  components: {
    TheSearchInput,
    TheSearchButton,
    TheSearchResult,
  },

  data() {
    return {
      keywords: [
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
