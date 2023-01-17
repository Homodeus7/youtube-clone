<template>
  <DropdownSettingsHeader
    title="Choose yor location"
    @back="$emit('select-menu', 'main')"
  />
  <section class="py-2">
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingsListItem
        v-for="(locationName, locationId) in locations"
        :key="locationId"
        :label="locationName"
        :active="locationId === selectedOptions.location.id"
        @click="selectOption({ id: locationId, text: locationName })"
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
      locations: ["Turkey", "United States", "Russia"],
    };
  },

  methods: {
    selectOption(location) {
      this.$emit("select-option", { name: "location", value: location });
      //this.selectedThemeId = themeId;
    },
  },
};
</script>
