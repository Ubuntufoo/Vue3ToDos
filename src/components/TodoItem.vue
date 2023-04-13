<script setup>
import { Icon } from '@iconify/vue';
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
  index: {
    type: Number,
    required: true,
  },
});

defineEmits(['toggle-complete', 'edit-todo', 'update-todo', 'delete-todo']);

</script>

<template>
  <li>
    <input type="checkbox" :checked="todo.isCompleted" @input="$emit('toggle-complete', index)" />
    <div class="todo">
      <input v-if="todo.isEditing" type="text" :value="todo.todo"
        @input="$emit('update-todo', $event.target.value, index)" />
      <span v-else :class="{ 'completed-todo': todo.isCompleted }">
        {{ todo.todo }}
      </span>
    </div>
    <div class="todo-actions">
      <Icon v-if="todo.isEditing" @click="$emit('edit-todo', index)" icon="line-md:confirm-circle" class="icon"
        color="#6be585" width="22" />
      <Icon v-else @click="$emit('edit-todo', index)" icon="line-md:edit" class="icon" color="black" width="22" />
      <Icon @click="$emit('delete-todo', todo.id)" icon="line-md:close-circle" class="icon" color="#dd3e54" width="22" />
    </div>
  </li>
</template>

<style lang="scss" scoped>
li {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 16px 10px;
  background-color: #f1f1f1;
  box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.4),
    0 8px 10px -6px rgb(0 0 0 / 0.4);

  &:hover {
    .todo-actions {
      opacity: 1;
    }
  }

  input[type="checkbox"] {
    appearance: none;
    width: 20px;
    height: 20px;
    background-color: #fff;
    border-radius: 50%;
    box-shadow: 0 4px 6px 0px rgb(0 0 0 / 0.5), 0 2px 4px -2px rgb(0 0 0 / 0.5);

    &:checked {
      background-color: #6be585;
    }
  }

  .todo {
    flex: 1;

    .completed-todo {
      opacity: 0.3;
    }

    input[type="text"] {
      width: 100%;
      padding: 2px 6px;
      border: 2px solid #41b080;
    }
  }

  .todo-actions {
    display: flex;
    gap: 6px;
    opacity: 0;
    transition: 150ms ease-in-out;

    .icon {
      cursor: pointer;
    }
  }
}
</style>
