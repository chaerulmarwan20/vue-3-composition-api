<template></template>

<script>
import {
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted,
  onActivated,
  onDeactivated,
  onErrorCaptured,
} from "vue";

export default {
  setup() {
    onBeforeMount(() => {
      console.log("onBeforeMount");
    });
    onMounted(() => {
      console.log("onMounted");
    });
    onBeforeUpdate(() => {
      console.log("onBeforeUpdate");
    });
    onMounted(() => {
      console.log("onMounted");
    });
    onUpdated(() => {
      console.log("onUpdated");
    });
    onBeforeUnmount(() => {
      console.log("onBeforeUnmount");
    });
    onUnmounted(() => {
      console.log("onUnmounted");
    });
    onActivated(() => {
      // dijalankan ketika keep-alive diaktifkan
      console.log("onActivated");
    });
    onDeactivated(() => {
      // dijalankan ketika keep-alive dinonaktifkan
      console.log("onDeactivated");
    });
    onErrorCaptured(() => {
      // dijalankan ketika ada error di child component
      console.log("onErrorCaptured");
    });
  },
};
</script>
