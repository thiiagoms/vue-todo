<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th scope="col">Task</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index">
          <td>{{ task }}</td>
          <td>
            <button type="button" class="btn btn-danger btn-sm" @click="handleDestroy(index)">
              <font-awesome-icon icon="fa-solid fa-trash" />
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TableComponent',
  props: {
    tasks: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    handleDestroy(index: number) {
      let tasksCopy = [...this.tasks]
      tasksCopy.splice(index, 1)
      this.$emit('update:tasks', tasksCopy)
    }
  }
})
</script>
