<template>
    <div class="description">
        {{ todo.description }}
        <span class="created-on">
          (created on {{ moment(todo.createdOn).format('DD-MM-YYYY HH:mm') }})
        </span>
      </div>
      <div class="todo-action">
        <span
          class="fa"
          :class="[todo.finishedOn ? 'fa-check-square checked' : 'fa-square']"
          @click="changeTodo(todo)"></span>
    </div>
</template>

<script>
import moment from 'moment';

export default {
    name: 'TodoItem',
    props: ['todo'],
    emits: ["change-todo"],
    data() {
        return{
            moment
        }
    },
    methods: {
        changeTodo() {
            this.$emit('change-todo', this.todo)
        },
    }
}
</script>

<style scoped>
  .description {
    font-size: 1rem;
  }
  .description > .created-on {
    display: block;
    font-size: .9rem;
    color: #999;
    font-style: italic;
  }
  .todo-action {
    font-size: 1.3rem;
  }
  .checked {
    color: #3eaf7c
  }
</style>