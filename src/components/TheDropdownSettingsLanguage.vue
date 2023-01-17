<template>
  <DropdownSettingsHeader
    title="Choose yor language"
    @back="$emit('select-menu', 'main')"
  />
  <section class="py-2">
    <ul>
      <DropdownSettingsListItem
        v-for="(languageName, languageId) in languages"
        :key="languageId"
        :label="languageName"
        :active="languageId === selectedLanguageId"
        @click="selectedLanguageId = languageId"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingsListItem from "./DropdownSettingsListItem.vue";
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";

export default {
  props: ["icon", "label"],

  components: {
    DropdownSettingsListItem,
    DropdownSettingsHeader,
  },

  emits: ["select-menu"],

  data() {
    return {
      selectedLanguageId: 0,
      languages: ["English", "Russian"],
    };
  },
};
</script>
