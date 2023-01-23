<template>
  <div class="fixed inset-0 z-10 bg-black bg-opacity-80">
    <div class="bg-white max-w-sm mx-auto my-8">
      <div class="p-2 text-right">
        <BaseModalButtonClose />
      </div>
      <div class="p-6">
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Deleniti,
        placeat. Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ipsa
        illo doloremque eaque eum asperiores aspernatur accusamus voluptatem
        maiores obcaecati dicta! Lorem ipsum dolor sit, amet consectetur
        adipisicing elit. Ipsa illo doloremque eaque eum asperiores aspernatur
        accusamus voluptatem maiores obcaecati dicta!
      </div>
    </div>
  </div>
</template>

<script>
import BaseModalButtonClose from "./BaseModalButtonClose.vue";

export default {
  components: {
    BaseModalButtonClose,
  },
};
</script>
