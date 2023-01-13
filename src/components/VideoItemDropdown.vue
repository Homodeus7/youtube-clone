<template>
  <div class="relative ml-auto">
    <button @click="toggle" :class="buttonClasses">
      <BaseIcon name="dotsVertical" />
    </button>
    <transition
      enter-active-class="transition ease-out duration-100"
      enter-from-class="transition opacity-0 scale-95"
      enter-to-class="transform opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75"
      leave-from-class="transform opacity-100 scale-100"
      leave-to-class="transition opacity-0 scale-95"
    >
      <div
        v-show="isOpen"
        ref="dropdown"
        @keydown.esc="isOpen = false"
        tabindex="-1"
        :class="dropdownClasses"
      >
        <section class="py-2">
          <ul>
            <VideoItemDropdownListItem label="Add to queue" icon="menuAlt3" />
          </ul>
        </section>
      </div>
    </transition>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import VideoItemDropdownListItem from "./VideoItemDropdownListItem.vue";

export default {
  components: {
    BaseIcon,
    VideoItemDropdownListItem,
  },
  data() {
    return {
      isOpen: false,
      positionClasses: [],
    };
  },
  mounted() {
    window.addEventListener("click", (event) => {
      if (!this.$el.contains(event.target)) {
        this.isOpen = false;
      }
    });
  },
  watch: {
    isOpen() {
      document.body.classList.toggle("overflow-hidden");

      this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus());
    },
  },
  computed: {
    buttonClasses() {
      return [
        "p-1",
        "text-gray-500",
        "hover:text-gray-700",
        "focus:outline-none",
        "group-hover:opacity-100",
        this.isOpen ? "opacity-100" : "opacity-0",
      ];
    },

    dropdownClasses() {
      return [
        "z-30",
        "absolute",
        // "top-9",
        // "-right-full",
        // "sm:right-0",
        "bg-white",
        "w-48",
        "rounded",
        "shadow",
        "focus:outline-none",
        ...this.positionClasses,
      ];
    },
  },
  methods: {
    toggle(event) {
      this.isOpen = !this.isOpen;

      if (this.isOpen) {
        this.$nextTick(() => {
          this.positionClasses = this.getPositionClasses(event);
        });
      }
    },

    getPositionClasses(event) {
      return [
        this.getTopClass(event),
        this.getRightClass(event),
        this.getLeftClass(event),
        this.getBottomClass(event),
      ];
    },

    getTopClass(event) {
      const clickCoordY = event.clientY; // vertical coordinate of click
      const buttonHeight = event.currentTarget.offsetHeight; // button height
      const dropdownHeight = this.$refs.dropdown.offsetHeight;

      if (window.innerHeight - clickCoordY < dropdownHeight) {
        // отнимаем от высоты окна вертикальную координату клика(получется расстояние
        // от клика до конца страницы) и если это расстояние меньше, чем выпадающий список
        // то мы смещаем список выше кнопки открытия
        return "top-auto";
      }
      if (window.innerHeight - clickCoordY < dropdownHeight + buttonHeight) {
        // если растояние низа страницы и вертикальной координатой клика будет меньше
        //  чем суммарная высота выпадающего списка и кнопки открытия этого списка
        return "top-0";
      }
      return "top-8";
    },

    getRightClass(event) {
      const clickCoordX = event.clientX;
      const clickCoordY = event.clientY;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;
      const buttonHeight = event.currentTarget.offsetHeight;

      if (window.innerWidth - clickCoordX > dropdownWidth) {
        return "right-auto";
      }

      if (window.innerHeight - clickCoordY > dropdownHeight + buttonHeight) {
        return "right-0";
      }

      if (window.innerHeight - clickCoordY > dropdownHeight) {
        return "right-8";
      }
      return "right-0";
    },

    getLeftClass(event) {
      const clickCoordX = event.clientX;
      const clickCoordY = event.clientY;
      const buttonHeight = event.currentTarget.offsetHeight;
      const dropdownWidth = this.$refs.dropdown.offsetWidth;
      const dropdownHeight = this.$refs.dropdown.offsetHeight;

      if (window.innerWidth - clickCoordX < dropdownWidth) {
        return "left-auto";
      }

      if (window.innerHeight - clickCoordY < dropdownHeight) {
        return "left-auto";
      }

      if (window.innerHeight - clickCoordY > dropdownHeight + buttonHeight) {
        return "left-auto";
      }

      return "left-8";
    },

    getBottomClass(event) {
      if (window.innerHeight - clickCoordY < dropdownHeight) {
        return "bottom-9";
      }

      return "bottom-auto";
    },
  },
};
</script>
