<template>
  <div v-for="item in items" :key="item.id">
    {{ item.id }}: {{ item.title }}
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import { TodoItem } from '../types'

export default defineComponent({
  props: {
    items: Array as PropType<TodoItem[]>
  },

  setup() {

  }
})
</script>

<style scoped>

</style>
