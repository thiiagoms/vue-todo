<template>
  <div class="container" style="max-width: 600px">
    <h2 class="text-center mt-5">Vue Todo App</h2>
    <div class="d-flex mt-5">
      <input type="text" class="w-100 form control" v-model="form.task" placeholder="Task name" />
      <button
        type="button"
        class="btn btn-primary btn-lg"
        style="margin-left: 5px"
        @click="handleTask()"
      >
        <font-awesome-icon icon="fa-solid fa-plus" />
      </button>
    </div>
    <TableComponent :tasks="model.tasks" @update:tasks="updateTasks" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TableComponent from './Table.vue'

export default defineComponent({
  name: 'TodoComponent',
  components: {
    TableComponent
  },
  data: () => ({
    form: { task: '' } as { task: String },
    model: {
      tasks: []
    } as { tasks: String[] }
  }),
  methods: {
    handleTask() {
      if (this.form.task != '') {
        this.model.tasks.push(this.form.task)
        this.form.task = ''
      }
    },
    updateTasks(tasks: String[]) {
      this.model.tasks = tasks
    }
  }
})
</script>
