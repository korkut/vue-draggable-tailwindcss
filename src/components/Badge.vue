<template>
  <div class="relative inline-block text-left">
    <div v-show="task.dataIcon === 'check'" @click="handleChangeBadge">
      <Check></Check>
    </div>
    <div v-show="task.dataIcon === 'clock'" @click="handleChangeBadge">
      <Clock></Clock>
    </div>
    <div v-show="task.dataIcon === 'sort-alt'" @click="handleChangeBadge">
      <SortAlt></SortAlt>
    </div>
    <div v-show="task.dataIcon === 'exclamation'" @click="handleChangeBadge">
      <Exclamation></Exclamation>
    </div>
    <ChangeBadge :task="task" v-show="task.isShowChangeBadge" />
  </div>
</template>
<script>
import { Check, Clock, SortAlt, Exclamation } from "./icons";
import ChangeBadge from "./ChangeBadge";
export default {
  props: {
    task: { type: Object, default: null },
    columns: { type: Array, default: null },
  },
  methods: {
    handleChangeBadge() {
      setTimeout(() => {
        this.task.isShowChangeBadge = true;
      }, 0);
    },
  },
  mounted() {
    // console.log(this.columns);
  },
  components: {
    Check,
    Clock,
    SortAlt,
    Exclamation,
    ChangeBadge,
  },
  data() {
    return {};
  },
};
</script>
