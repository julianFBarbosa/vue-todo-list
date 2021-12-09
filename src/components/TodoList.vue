<script>
import ListItem from "./ListItem.vue";
export default {
  components: {
    ListItem,
  },
  data() {
    return {
      todoList: JSON.parse(localStorage.items) || [],
      todoItem: "",
    };
  },
  methods: {
    addItem() {
      if (this.todoItem) {
        this.todoList.push({ key: this.uuid(), text: this.todoItem });
        this.todoItem = "";
        localStorage.items = JSON.stringify(this.todoList);
        this.$refs.todoInput.focus();
      }
    },

    removeItem({ key }) {
      if (!key) return;
      const itemIndex = this.todoList.map(({ key }) => key).indexOf(key);

      this.todoList.splice(itemIndex, 1);
      localStorage.items = JSON.stringify(this.todoList);
    },

    uuid() {
      const head = Date.now().toString(36);
      const tail = Math.random().toString(36).substr(2);

      return head + tail;
    },
  },
  computed: {
    invertedTodoList() {
      return [...this.todoList].reverse();
    },
  },
};
</script>

<template>
  <h1 class="title">A simple Vue to-do list</h1>

  <div class="wrapper">
    <input
      type="text"
      class="input"
      name="todo-item"
      id="todo-item"
      ref="todoInput"
      v-model="todoItem"
    />
    <button class="button" v-on:click="addItem">Add item</button>
  </div>

  <ul class="list" v-if="todoList.length > 0">
    <ListItem
      v-for="item in this.invertedTodoList"
      :item="item"
      :list="todoList"
      @remove-item="removeItem"
    />
  </ul>
  <p v-else>You don't have any tasks yet.</p>
</template>

<style lang="scss" scoped>
@import "../styles/variables";

.list {
  padding: 0;
  max-width: 90%;
  margin: 0 auto;

  li {
    padding: 0;
  }
}

.wrapper {
  display: flex;
  gap: 0.5rem 1rem;
  max-width: 90%;
  margin: 0 auto 16px;
}

.title {
  color: $blue-700;
  margin-bottom: 16px;
}

.input {
  margin: 0;
  display: block;
  flex: 1;
  padding: 0.5rem;
  padding-left: 0.2rem;
  color: $blue-100;
  background: $blue-1000;
  outline: none;
  border: 2px solid $blue-700;
  border-radius: 4px;

  &:focus-visible,
  &:hover {
    box-shadow: 0 0 0 2px $blue-400;
    border-color: $blue-500;
  }
}

.button {
  padding: 8px 16px;
  border: none;
  background: $blue-900;
  color: $blue-200;
  font-weight: 550;
}
</style>
