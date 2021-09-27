<template>
  <div id="app" class="space-x-4 p-4">
    <div class="flex flex-wrap items-start py-6">
      <draggable
        :list="columns"
        :animation="200"
        ghost-class="ghost-card"
        group="colums"
        class="flex"
      >
        <div
          class="flex flex-col items-center cursor-move"
          v-for="column in columns"
          :key="column.title"
        >
          <div
            class="rounded-lg px-5 column-width py-5 rounded mr-4 dark:bg-[#797e93] bg-[#e9edf3]"
          >
            <h3
              class="
              font-bold
              dark:font-semibold
              text-sm text-gray-700
              dark:text-white
            "
            >
              {{ column.title }}
            </h3>
            <!-- Draggable component comes from vuedraggable. It provides drag & drop functionality -->
            <draggable
              :list="column.tasks"
              :animation="200"
              ghost-class="ghost-card"
              group="tasks"
            >
              <!-- Each element from here will be draggable and animated. Note :key is very important here to be unique both for draggable and animations to be smooth & consistent. -->
              <task-card
                v-for="task in column.tasks"
                :key="task.id"
                :task="task"
                :columns="columns"
                class="mt-3 cursor-move"
              ></task-card>
              <!-- </transition-group> -->
            </draggable>
          </div>
          <button
            type="button"
            class="
            inline-flex
            items-center
            p-2
            border-2
            my-4
            border-dashed border-gray-500
            text-gray-500
            hover:text-gray-600 hover:border-gray-600
            rounded-full
            shadow-sm
            focus:outline-none
          "
            v-on:click="addTask(column)"
          >
            <svg
              class="h-5 w-5"
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 20 20"
              fill="currentColor"
              aria-hidden="true"
            >
              <path
                fill-rule="evenodd"
                d="M10 5a1 1 0 011 1v3h3a1 1 0 110 2h-3v3a1 1 0 11-2 0v-3H6a1 1 0 110-2h3V6a1 1 0 011-1z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </button>
        </div>
      </draggable>
      <div
        class="
          flex
          items-center
          space-x-2
          py-2
          px-4
          w-[350px]
          bg-gray-200
          text-gray-500
          cursor-pointer
          dark:bg-[#797e93]
          dark:hover:bg-gray-500
          dark:text-white
        "
      >
        <svg
          class="h-5 w-5"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 20 20"
          fill="currentColor"
          aria-hidden="true"
        >
          <path
            fill-rule="evenodd"
            d="M10 5a1 1 0 011 1v3h3a1 1 0 110 2h-3v3a1 1 0 11-2 0v-3H6a1 1 0 110-2h3V6a1 1 0 011-1z"
            clip-rule="evenodd"
          ></path>
        </svg>
        <input
          class="outline-none bg-gray-200 focus:bg-white dark:bg-[#797e93] dark:text-white"
          placeholder="Add new list"
          @keydown.enter="handleEnter"
        />
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import TaskCard from "./components/TaskCard.vue";
export default {
  name: "App",
  components: {
    TaskCard,
    draggable,
  },
  mounted() {
    // if (
    //   localStorage.theme === "dark" ||
    //   (!("theme" in localStorage) &&
    //     window.matchMedia("(prefers-color-scheme: dark)").matches)
    // ) {
    //   document.documentElement.classList.add("dark");
    // } else {
    //   document.documentElement.classList.remove("dark");
    // }
    // localStorage.theme = "dark";
  },
  methods: {
    addTask(column) {
      column.tasks.push({
        user: "Unknown",
        title: "New Task",
        dataIcon: "clock",
        isShowChangeBadge: false,
      });
    },
    handleEnter(event) {
      this.columns.push({
        title: event.target.value,
        tasks: [],
      });
      event.target.value = "";
    },
  },
  data() {
    return {
      columns: [
        {
          title: "Backlog",
          tasks: [
            {
              id: 1,
              user: "Mehmet",
              title: "Add discount code to checkout page",
              dataIcon: "clock",
              isShowChangeBadge: false,
            },
            {
              id: 2,
              user: "Hüseyin",
              title: "Provide documentation on integrations",
              dataIcon: "check",
              isShowChangeBadge: false,
            },
          ],
        },
        {
          title: "In Progress",
          tasks: [
            {
              id: 3,
              user: "Hüseyin",
              title: "check shopping cart dropdown",
              dataIcon: "exclamation",
              isShowChangeBadge: false,
            },
            {
              id: 4,
              user: "Mehmet",
              title: "Add discount code to checkout page",
              dataIcon: "clock",
              isShowChangeBadge: false,
            },
          ],
        },
        {
          title: "Review",
          tasks: [
            {
              id: 5,
              user: "Hüseyin",
              title: "Provide documentation on integrations",
              dataIcon: "check",
              isShowChangeBadge: false,
            },
            {
              id: 6,
              user: "Mehmet",
              title: "check shopping cart dropdown",
              dataIcon: "sort-alt",
              isShowChangeBadge: false,
            },
          ],
        },
        {
          title: "Done",
          tasks: [
            {
              id: 7,
              user: "Hüseyin",
              title: "Add discount code to checkout page",
              dataIcon: "clock",
              isShowChangeBadge: false,
            },
            {
              id: 8,
              user: "Mehmet",
              title: "check shopping cart dropdown",
              dataIcon: "check",
              isShowChangeBadge: false,
            },
          ],
        },
      ],
    };
  },
};
</script>

<style scoped>
.column-width {
  min-width: 320px;
  width: 320px;
}
/* Unfortunately @apply cannot be setup in codesandbox, 
but you'd use "@apply border opacity-50 border-blue-500 bg-gray-200" here */
.ghost-card {
  opacity: 0.5;
  background: #f7fafc;
  border: 1px solid #4299e1;
}
</style>
