<template>
  <div class="cursor-default">
    <div
      class="
                  absolute
                  left-0
                  top-0
                  ml-10
                  rounded-lg
                  shadow-lg
                  bg-white
                  dark:bg-[#4b4e69] dark:text-white
                  ring-1 ring-black ring-opacity-5
                  focus:outline-none
                "
      role="menu"
      aria-orientation="vertical"
      aria-labelledby="menu-button"
      tabindex="-1"
    >
      <div class="p-4 space-y-4" role="none">
        <div
          class="flex space-x-3 hover:bg-gray-100 cursor-pointer"
          @click="handleChangeBadge('exclamation')"
        >
          <Exclamation />
          <span>Upcoming</span>
        </div>

        <div
          class="flex space-x-3 hover:bg-gray-100 cursor-pointer"
          @click="handleChangeBadge('sort-alt')"
        >
          <SortAlt />
          <span>Progress</span>
        </div>

        <div
          class="flex space-x-3 hover:bg-gray-100 cursor-pointer"
          @click="handleChangeBadge('clock')"
        >
          <Clock />
          <span>Finish</span>
        </div>

        <div
          class="flex space-x-3 hover:bg-gray-100 cursor-pointer"
          @click="handleChangeBadge('check')"
        >
          <Check />
          <span>Approved</span>
        </div>

        <div class="text-blue-500 dark:text-white font-semibold">
          + new
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { Check, Clock, SortAlt, Exclamation } from "./icons";
export default {
  components: {
    Check,
    Clock,
    SortAlt,
    Exclamation,
  },
  props: {
    task: { type: Object, default: null },
  },
  methods: {
    handleChangeBadge(iconName) {
      this.task.isShowChangeBadge = false;
      this.task.dataIcon = iconName;
    },
  },
};
</script>
