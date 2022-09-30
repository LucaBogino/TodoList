<template>
    <TodoForm @add-todo="addTodo"/>

    <div class="todo-list">
        <div class="todo-item" v-for="todo in todos" :key="todo.id">
          <TodoItem 
            :key="todo.id" 
            :todo="todo"
            @change-todo="changeTodo"></TodoItem>
        </div>
    </div>
</template>
  
<script>
  import TodoForm from './TodoForm.vue';
  import TodoItem from './TodoItem.vue';

  export default {
    components: {
        TodoForm,
        TodoItem        
    },
    data() {
      return {
          todos: [
                    {
                      id: 1664543434837,
                      description: 'Follow Luca Bogino on GitHub',
                      createdOn: 1664543434837,
                      finishedOn: null
                    },
          ],
      }
  },
  methods: {
      changeTodo(todo) {
          todo.finishedOn = !todo.finishedOn ? new Date() : null
      },
      addTodo(newTodo) {
        const todo = {
          id: Date.now(),
          description: newTodo,
          createdOn: new Date().getTime(),
          finishedOn: null
        }

        this.todos.push(todo)
      }
  }
}
</script>

<style scoped>
  .todo-list {
    display: flex;
    flex-direction: column; 
    align-items: center;
    align-content: center;
    align-self: center;
  }
  .todo-item {
    display: flex;
    flex-direction: row;
    align-items: center;
    align-content: space-between;
    justify-content: space-between;
    margin: 10px 10px;
    border: 1px solid #c9c9c9;
    padding: 20px;
    width: 40%;
    text-align: left;
  }
</style>
