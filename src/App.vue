<template>
  <div>Count : {{ nilai }}</div>
  <button type="button" @click="add">Add</button>
  <div>Result : {{ result }}</div>
</template>

<script>
import { reactive, ref, computed, toRefs } from "vue";

export default {
  setup() {
    const counter = reactive({
      nilai: 0,
    });
    const addNum = ref(1);

    const add = () => {
      result.value = 5;
      counter.nilai++;
    };

    const result = computed({
      get: () => {
        return counter.nilai + addNum.value;
      },
      set: (val) => {
        addNum.value = val;
      },
    });

    return {
      ...toRefs(counter),
      add,
      result,
    };
  },
};
</script>
