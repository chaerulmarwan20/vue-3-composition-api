<template>
  <user-component :label="label" :user="user" class="active" @submit="onSubmit">
    <div>Slot</div>
  </user-component>
  <button type="button" @click="changeName">Change</button>
</template>

<script>
import { ref, reactive } from "vue";
import UserComponent from "./components/UserComponent.vue";

export default {
  components: { UserComponent },
  setup() {
    const label = ref("biodata");
    const user = reactive({
      name: "Chaerul",
      age: 22,
    });

    const changeName = () => {
      user.name = "Marwan";
    };

    const onSubmit = (val) => {
      console.log(val);
    };

    return {
      label,
      user,
      changeName,
      onSubmit,
    };
  },
};
</script>
