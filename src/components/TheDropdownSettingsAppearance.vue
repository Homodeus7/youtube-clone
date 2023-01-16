<template>
  <section class="py-2 border-b">
    <ul>
      <DropdownSettingsListItem
        v-for="listItem in listItems.slice(0, 8)"
        :key="listItem.label"
        :label="listItem.label"
      />
    </ul>
  </section>
</template>

<script>
import DropdownSettingsListItem from "./DropdownSettingsListItem.vue";

export default {
  props: ["icon", "label"],

  components: {
    DropdownSettingsListItem,
  },

  data() {
    return {
      listItems: [
        {
          label: "Use devise theme",
        },
        {
          label: "Dark theme",
        },
        {
          label: "Light theme",
        },
      ],
    };
  },
};
</script>
