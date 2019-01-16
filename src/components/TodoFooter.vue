<template>
  <div class="todo-footer">
    <button type="button" class="btn-clear" v-on:click="clearTodo">모든 일정 지우기</button>
  </div>
</template>

<script>
export default {
 methods: {
   clearTodo() {
     this.$emit('removeAll');
   }
 }
}
</script>

<style lang="scss" scoped="scoped">
  .todo-footer{
    padding-bottom: 2rem;
    text-align: center;
  }

  .btn-clear{
    padding: 1rem;
    color: #fff;
    font-weight: bold;
    background: #2354e7;
    border-radius: 5px;
    cursor: pointer;
  }
</style>
