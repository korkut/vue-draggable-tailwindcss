<template>
  <div
    class="flex items-center justify-between rounded bg-white dark:bg-[#4b4e69] dark:border dark:border-transparent dark:hover:border-white shadow hover:shadow-lg transition duration-300 ease-in-out p-4 pl-10"
  >
    <div
      class="font-bold text-sm text-gray-700 dark:font-semibold dark:text-white"
    >
      <p
        class="hover:bg-gray-100 focus:bg-gray-100 dark:bg-[#4b4e69] dark:text-white outline-none text-sm text-gray-700 hover:cursor-text"
        contenteditable
        @blur="(event) => (task.title = event.target.innerText)"
      >
        {{ task.title }}
      </p>
      <p
        class="hover:bg-gray-100 focus:bg-gray-100 dark:bg-[#4b4e69] dark:text-white outline-none text-sm text-gray-700 hover:cursor-text"
        contenteditable
        @blur="(event) => (task.description = event.target.innerText)"
      >
        {{ task.description }}
      </p>
    </div>
    <Badge :columns="columns" :task="task"></Badge>
  </div>
</template>
<script>
import Badge from "./Badge.vue";
export default {
  components: {
    Badge,
  },
  props: {
    task: {
      type: Object,
      default: () => ({}),
    },
    columns: {
      type: Array,
      default: null,
    },
  },
  methods: {},
  computed: {},
};
</script>
<style scoped>
p {
  width: 11rem;
}
</style>
