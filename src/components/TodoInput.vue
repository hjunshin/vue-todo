<template>
<div class="todo-input">
  <input type="text" placeholder="할 일을 추가해 보즈아!!" v-model="newTodoItem" v-on:keyup.enter="addTodo">
  <button type="button" title="일정 추가" v-on:click="addTodo">
    <i class="material-icons" aria-hidden="true">add</i>
  </button>
</div>
</template>

<script>
export default {
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
        this.$emit('addTodo', value);
        this.clearInput();
      }
    },
    clearInput() {
      this.newTodoItem = '';
    }

  }
}
</script>

<style lang="scss" scoped="scoped">
$color: #2354e7;

.todo-input {
    position: relative;
    margin: 2rem 0;
    font-size: 0;
    text-align: center;
    overflow: hidden;

    & > input[type=text] {
        padding: 0 52px 0 20px;
        width: 100%;
        height: 4rem;
        font-size: 20px;
        line-height: 4rem;
        border: 0 none;
        border-radius: 5px;
        box-sizing: border-box;
    }

    & > button {

        position: absolute;
        right: 0;
        top: 0;
        background: $color;
        border-radius: 0 5px 5px 0;
        cursor: pointer;

        & > .material-icons {
            color: #fff;
            font-size: 4rem;
            vertical-align: top;
        }

    }
}
</style>
