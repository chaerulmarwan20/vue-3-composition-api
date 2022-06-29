<template>
  <div style="margin-top: 20px">
    <ul class="list-group">
      <li class="list-group-item" v-for="(todo, idx) in todos" :key="idx">
        <div class="row">
          <div class="col">
            <span v-if="todo.isDone">
              <del>{{ todo.activity }}</del>
            </span>
            <span v-else>
              {{ todo.activity }}
            </span>
          </div>
          <div class="col-auto">
            <div class="row gx-2">
              <div class="col">
                <button type="button" class="btn btn-info" @click="done(idx)">
                  Done
                </button>
              </div>
              <div class="col">
                <button
                  type="button"
                  class="btn btn-danger"
                  @click="deleteTodo(idx)"
                >
                  X
                </button>
              </div>
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      default: [],
    },
  },
  setup(props, { emit }) {
    const deleteTodo = (idx) => {
      emit("deleteTodo", idx);
    };

    const done = (idx) => {
      emit("doneTodo", idx);
    };

    return { deleteTodo, done };
  },
};
</script>
