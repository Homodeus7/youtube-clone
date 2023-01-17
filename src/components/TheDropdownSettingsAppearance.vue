<template>
  <DropdownSettingsHeader
    title="Appearance"
    @back="$emit('select-menu', 'main')"
  />
  <section class="py-2">
    <div class="text-gray-500 text-xs p-3">
      Setting applies to this browser only
    </div>
    <ul>
      <DropdownSettingsListItem
        v-for="(themeName, themeId) in themes"
        :key="themeId"
        :label="themeName"
        :active="themeId === selectedOptions.theme.id"
        @click="selectOption({ id: themeId, text: themeName })"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingsListItem from "./DropdownSettingsListItem.vue";
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";

export default {
  components: {
    DropdownSettingsListItem,
    DropdownSettingsHeader,
  },

  props: ["selectedOptions"],

  emits: ["select-menu", "select-option"],

  data() {
    return {
      themes: ["Devise theme", "Dark theme", "Light theme"],
    };
  },

  methods: {
    selectOption(theme) {
      this.$emit("select-option", { name: "theme", value: theme });
      //this.selectedThemeId = themeId;
    },
  },
};
</script>
