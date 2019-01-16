<template>
<div class="todo-list">
  <ul class="list">
    <li v-for="(todoItem, index) in propsdata">
      <i class="ico-label material-icons" aria-hidde="true">label</i>
      {{ todoItem }}
      <button type="button" class="btn-delete" title="해당 일정 삭제" v-on:click="removeTodo(todoItem, index)">
        <i class="material-icons" aria-hidde="true">delete_forever</i>
      </button>
    </li>
  </ul>
</div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    }
  }
}
</script>

<style lang="scss" scoped="scoped">
.todo-list {

    padding: 2rem 0;

    & > .list > li {
        position: relative;
        margin-top: 1rem;
        padding: 0 4rem 0 3rem;
        min-height: 4rem;
        font-size: 24px;
        line-height: 4rem;
        background: #fff;
        border-radius: 5px;
        box-sizing: border-box;
        overflow: hidden;

        &:first-child {
            margin-top: 0;
        }

        .ico-label {
            position: absolute;
            left: 0;
            top: 0;
            padding-left: 1rem;
            color: #ffc800;
            vertical-align: middle;
            line-height: inherit;
        }
    }

    .btn-delete {
        position: absolute;
        right: 0;
        top: 0;
        width: 4rem;
        height: 100%;
        background: #9a2013;
        cursor: pointer;

        & > .material-icons {
            color: #fff;
            font-size: 3rem;
            vertical-align: middle;
        }
    }
}
</style>
