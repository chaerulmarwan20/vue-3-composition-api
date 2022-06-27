<template>
  <div>Count : {{ nilai }}</div>
  <button type="button" @click="add">Add</button>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const counter = reactive({
      nilai: 0,
    });

    const add = () => {
      counter.nilai++;
    };

    return {
      ...toRefs(counter),
      add,
    };
  },
};
</script>
