<template>
  <div>Name : {{ name }}</div>
  <div>Age : {{ age }}</div>
</template>

<script>
import { reactive, toRefs } from "vue";

export default {
  setup() {
    const user = reactive({
      name: "Chaerul",
      age: "22",
    });

    setTimeout(() => {
      user.name = "Marwan";
    }, 2000);

    return {
      ...toRefs(user),
    };
  },
};
</script>
