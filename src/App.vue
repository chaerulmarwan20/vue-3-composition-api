<template>
  <div>Count : {{ nilai }}</div>
  <button type="button" @click="add">Add</button>
</template>

<script>
import { reactive, watchEffect, toRefs } from "vue";

export default {
  setup() {
    const counter = reactive({
      nilai: 0,
      foo: "bar",
    });

    const add = () => {
      counter.nilai++;
    };

    watchEffect(
      () => {
        console.log(counter.nilai);
      },
      {
        flush: "post",
        onTrigger(e) {
          console.log("onTrigger", e);
        },
        onTrack(e) {
          console.log("onTrack", e);
        },
      }
    );

    return {
      ...toRefs(counter),
      add,
    };
  },
};
</script>
