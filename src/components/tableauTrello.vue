<script lang="ts" setup>
import { ref } from 'vue'
import { Column } from '../types'
import { VueDraggable } from 'vue-draggable-plus'
import TacheTrelloVue from '../components/tacheTrello.vue'

const columns = ref<Array<Column>>([
  {
    id: 1,
    title: 'A venir 👇🏿',
    tasks: [
      {
        id: 1,
        title: 'Creer une app frontend',
        content: 'Developper une appli avec Vue 3 et API Composition'
      },
      { id: 2, title: 'Creer une app backend', content: 'Developper une appli avec Laravel 11' }
    ]
  },
  { id: 2, title: 'A faire ☝🏿', tasks: [] },
  { id: 3, title: 'Fait 👌🏿', tasks: [] }
])
</script>

<template>
  <VueDraggable
    v-model="columns"
    animation="150"
    ghostClass="ghost"
    handle=".cursor_emoji"
    group="columns"
    item-key="id"
    class="flex items-start space-x-4 mt-10"
  >
    <div
      v-for="column in columns"
      :key="column.id"
      class="bg-gray-50 rounded shadow min-w-[250px] p-5"
    >
      <span class="cursor_emoji hover:cursor-move bg-red-700 pr-2 pl-2 text-white">↔️</span>
      <header class="font-bold mb-5">{{ column.title }}</header>
      <VueDraggable
        v-model="column.tasks"
        animation="150"
        ghostClass="ghost"
        group="tasks"
        item-key="id"
        class="space-y-2"
      >
        <TacheTrelloVue v-for="task in column.tasks" :key="task.id" :task="task" />
      </VueDraggable>
    </div>
  </VueDraggable>
</template>
