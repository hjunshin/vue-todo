<template>
<div class="app-wrap">
  <header>
    <TodoHeader></TodoHeader>
  </header>

  <section>
    <div class="app-section">
      <TodoInput v-on:addTodo="addTodo"></TodoInput>
      <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo"></TodoList>
    </div>
  </section>

  <footer>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
  </footer>
</div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data() {
    return {
      todoItems: []
    }
  },
  created() {
    var storageLen = localStorage.length;
    if (storageLen > 0) {
      for (var i = 0; i < storageLen; i += 1) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods: {

    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    }

  },
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>


<style lang="scss" scoped="scoped">
.app-section {
    padding: 0 2rem;
}
</style>
