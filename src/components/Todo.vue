<template>
    <div class="todo__wrapper">
      <div class="todo__item">
        <label
          class="todo__title"
          :class="[todo.is_completed ? 'todo__title--check': '', 'todo__title' ]">
          <input
            type="checkbox"
            @click="$emit('toggle-todo', todo.id)"
            :checked="todo.is_completed"
            v-on:change="toggleTodo"
          >
          <div class="checkmark"></div>
          {{ todo.title }}
        </label>
      </div>
      <div class="deleteTodo__wrapper">
        <i 
          @click="$emit('delete-todo', todo.id)"
          :class="{'todo__item--delete': todo.is_completed}"
          class="delete__icon far fa-trash-alt"
        >
        </i>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Todo',
  props: {
    todo: Object
  },
  methods: {
    toggleTodo() {
      this.todo.is_completed = !this.todo.is_completed
    }
  }
}
</script>

<style scoped>
.todo__wrapper {
  display: flex;
  align-items: center;
  width: 330px;
  margin: 20px 0 20px 30px;
  /* justify-content: space-between; */
}

.todo__item {
  display: inline-flex;
  width: 100%;
  user-select: none;
}

.todo__title--check {
  text-decoration: line-through;
}

.todo__title {
  display: flex;
  color: #505050;
  font-weight: bold;
  font-size: 1.2em;
  cursor: pointer;
}

.todo__title:hover {
  color: #161616;
}

.deleteTodo__wrapper {
  font-size: 1.3em;
  color: #505050;
  margin-left: 5px;
}

.delete__icon {
  cursor: pointer;
  display: none;
}

.todo__item--delete {
  display: block;
  transition: .5s;
}
</style>