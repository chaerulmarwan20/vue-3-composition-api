<template>
  <div>{{ message }}</div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    const message = ref("Hello World");

    setTimeout(() => {
      message.value = "Halo Dunia";
    }, 2000);

    return {
      message,
    };
  },
};
</script>
