<script lang="ts" setup>
import { Task } from '../types'

defineProps<{
  task: Task
}>()
</script>
<template>
  <div
    class="bg-white rounded shadow min-w[250px] p-2 mb-2 hover:cursor-move"
    :title="task.content"
  >
    <input type="text" :value="task.title" @keyup.enter="$event.target.blur()" />
  </div>
</template>
