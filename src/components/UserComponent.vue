<template>
  <div>{{ label }} : {{ user.name }}</div>
  <div>{{ description }}</div>
  <button type="text" @click="submit">Submit</button>
  <hr />
  <slot />
</template>

<script>
import { toRefs, computed, onMounted } from "vue";

export default {
  props: {
    label: {
      type: String,
      default: "",
    },
    user: {
      type: Object,
      default: {},
    },
  },
  setup(props, context) {
    const { attrs, slots, emit } = context;
    const { label, user } = toRefs(props);
    const description = computed(() => {
      return `${label.value} : ${user.value.name}`;
    });

    onMounted(() => {
      console.log("attrs", attrs);
      console.log("slots", slots);
    });

    const submit = () => {
      emit("submit", "Emit from UserComponent");
    };

    return { description, submit };
  },
};
</script>
