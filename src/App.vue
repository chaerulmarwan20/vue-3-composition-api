<template>
  <div class="container" style="margin-top: 20px">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">SIMPLE TODO APP</h5>
        <div class="row">
          <div class="col-10">
            <input
              type="text"
              class="form-control"
              v-model="todo"
              @keyup.enter="add"
            />
          </div>
          <div class="col-2">
            <button type="button" class="btn btn-success" @click="add">
              ADD
            </button>
          </div>
        </div>
        <list :todos="list" @deleteTodo="deleteTodo" @doneTodo="doneTodo" />
        <br />
        <small>Total TODO : {{ totalTodo }}</small>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, reactive, computed, toRefs, onMounted, toRef } from "vue";
import List from "./components/List.vue";

export default {
  components: { List },
  setup() {
    const todo = ref("");
    const todos = reactive({
      list: [],
    });

    const totalTodo = computed(() => {
      return todos.list.length;
    });

    const add = () => {
      todos.list.unshift({ activity: todo.value, isDone: false });
      todo.value = "";
      saveToLocalStorage();
    };

    const deleteTodo = (todoIdx) => {
      todos.list = todos.list.filter((item, idx) => {
        if (idx !== todoIdx) {
          return item;
        }
      });
      saveToLocalStorage();
    };

    const doneTodo = (todoIdx) => {
      todos.list = todos.list.filter((item, idx) => {
        if (idx === todoIdx) {
          item.isDone = true;
        }
        return item;
      });
      saveToLocalStorage();
    };

    const saveToLocalStorage = () => {
      localStorage.setItem("todos", JSON.stringify(todos.list));
    };

    onMounted(() => {
      todos.list = JSON.parse(localStorage.getItem("todos") || []);
    });

    return { todo, ...toRefs(todos), totalTodo, add, deleteTodo, doneTodo };
  },
};
</script>
