<script setup>
import { ref, watch, computed } from 'vue';
import { uid } from 'uid';
import { Icon } from '@iconify/vue';
import TodoCreator from '../components/TodoCreator.vue';
import TodoItem from '../components/TodoItem.vue';
const todoList = ref([]);

watch(todoList,
  () => {
    setTodoListLocalStorage();
  }, {
  deep: true,
}
);

const todoCompleted = computed(() => {
  return todoList.value.every((todo) => todo.isCompleted);
})

const setTodoListLocalStorage = () => {
  localStorage.setItem('todoList', JSON.stringify(todoList.value));
};
const fetchTodoList = () => {
  const savedTodoList = JSON.parse(localStorage.getItem('todoList'));
  if (savedTodoList) {
    todoList.value = savedTodoList;
  }
};

fetchTodoList();

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });

};
const toggleTodoComplete = (todoPos) => {
  todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted;
};

const toggleEditTodo = (todoPos) => {
  todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing;
};

const updateTodo = (todoVal, todoPos) => {
  todoList.value[todoPos].todo = todoVal;
};

const deleteTodo = (todoId) => {
  todoList.value = todoList.value.filter((todo) => todo.id !== todoId)
};

</script>

<template>
  <main>
    <h1>Create something to do</h1>
    <TodoCreator @create-todo="createTodo" />
    <ul v-if="todoList.length > 0" class="todo-list">
      <TodoItem v-for="(todo, index) in todoList" :todo="todo" :index="index" @toggle-complete="toggleTodoComplete"
        @edit-todo="toggleEditTodo" @update-todo="updateTodo" @delete-todo="deleteTodo" />
    </ul>
    <p v-else class="todos-msg">
      <Icon icon="noto-v1:sad-but-relieved-face" color="#dd3e54" width="30" />
      <span>You have no to-do's!</span>
    </p>
    <p v-if="todoCompleted && todoList.length > 0" class="todos-msg">
      <Icon icon="noto-v1:party-popper" width="30" />
      <span>All to do's are done</span>
      <Icon icon="noto-v1:party-popper" width="30" />
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0 auto;
  padding: 40px 16px;

  h1 {
    margin: 60px 0px;
    text-align: center;
  }

  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }

  .todos-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>