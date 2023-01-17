<template>
  <DropdownSettingsHeader
    title="Choose yor language"
    @back="$emit('select-menu', 'main')"
  />
  <section class="py-2">
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingsListItem
        v-for="(languageName, languageId) in languages"
        :key="languageId"
        :label="languageName"
        :active="languageId === selectedOptions.languageId"
        @click="selectOption(languageId)"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingsListItem from "./DropdownSettingsListItem.vue";
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";

export default {
  props: ["selectedOptions"],

  components: {
    DropdownSettingsListItem,
    DropdownSettingsHeader,
  },

  emits: ["select-menu", "select-option"],

  data() {
    return {
      selectedLanguageId: 0,
      languages: ["English", "Russian"],
    };
  },

  methods: {
    selectOption(languageId) {
      this.$emit("select-option", { name: "languageId", value: languageId });
      //this.selectedThemeId = themeId;
    },
  },
};
</script>
