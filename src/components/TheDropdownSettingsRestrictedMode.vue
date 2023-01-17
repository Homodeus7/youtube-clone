<template>
  <DropdownSettingsHeader
    title="Restricted Mode"
    @back="$emit('select-menu', 'main')"
  />
  <section class="px-3 py-4 space-y-4 text-black text-sm">
    <p>This helps hide potentialy mature videos. No filter is 100% accurate.</p>
    <p>This settings only apples to this browser.</p>
    <div class="text-gray-600 font-semibold flex item-center">
      <span class="uppercase mr-2">Activate restricted mode</span>
      <input type="checkbox" />
    </div>
  </section>
</template>

<script>
import DropdownSettingsHeader from "./DropdownSettingsHeader.vue";

export default {
  props: ["icon", "label"],

  components: {
    DropdownSettingsHeader,
  },

  emits: ["select-menu"],
};
</script>
