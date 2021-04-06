<template>
  <h1 class="title">Todo app with Vite / Vue 3</h1>
  <div class="container">
    <h2 class="subtitle">All Todo</h2>
    <TodoList :items="todoItems" />

    <hr>

    <h2 class="subtitle">Completed Todo</h2>
    <TodoList :items="completedTodoItems" />
  </div>
</template>

<script lang="ts">
import { ref, defineComponent, onMounted, watch, computed } from 'vue'
import { TodoItem } from './types'
import TodoList from './components/TodoList.vue'

export default defineComponent({
  name: 'App',

  components: {
    TodoList
  },

  setup() {
    const todoItems = ref([] as TodoItem[])
    const initTodoItems = (): void => {
      todoItems.value = [
        {
          id: 1,
          title: 'Study Vite',
          isCompleted: false
        },
        {
          id: 2,
          title: 'Study Vue 3',
          isCompleted: true
        },
        {
          id: 3,
          title: 'Create Todo app',
          isCompleted: false
        },
      ]
    }

    const completedTodoItems = computed(() => {
      return todoItems.value.filter(item => {
        return item.isCompleted
      })
    })

    onMounted(initTodoItems)

    return {
      todoItems,
      completedTodoItems
    }
  },
})
</script>

<style scoped>
.title {
  text-align: center;
}

.container {
  max-width: 960px;
  margin: 0 auto;
  padding: 16px;
  background-color: #eceded;
  border: 1px solid #eceded;
  border-radius: 10px;
}

.subtitle {

}
</style>