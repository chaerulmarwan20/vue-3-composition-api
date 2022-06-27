<template>
  <div>Count : {{ nilai }}</div>
  <button type="button" @click="add">Add</button>
</template>

<script>
import { reactive, ref, watch, toRefs } from "vue";

export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: "bar",
    });
    const num1 = ref(1);
    const num2 = ref(2);

    const add = () => {
      // counter.nilai++;
      num1.value++;
      num2.value++;
    };

    // watch(num1, (after, before) => {
    //   console.log(num1.value);
    //   console.log("after", after);
    //   console.log("before", before);
    // });

    // watch(
    //   () => counter.nilai,
    //   (after, before) => {
    //     console.log(counter.nilai);
    //     console.log("after", after);
    //     console.log("before", before);
    //   }
    // );

    watch([num1, num2], (after, before) => {
      console.log("num1", num1.value);
      console.log("num2", num2.value);
      console.log("after", after);
      console.log("before", before);
    });

    return {
      ...toRefs(counter),
      add,
    };
  },
};
</script>
