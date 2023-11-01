<template>
  <div>
    <h2 class="mb-4">Task List</h2>
    <table class="table" >
      <thead>
        <tr>
          <th scope="col">No.</th>
          <th scope="col">Todo item</th>
          <th scope="col">Status</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <task-item
          v-for="(task, index) in tasks"
          :key="task.id"
          :task="task"
          @delete-task="deleteTask(index)"
        ></task-item>
      </tbody>
    </table>
    <button @click="getTasks" class="btn btn-warning">Get tasks</button>
  </div>
</template>

<script>
import TaskItem from './TaskItem.vue';

export default {
  props: {
    tasks: Array
  },
  components: {
    TaskItem
  },
  methods: {
    deleteTask(index) {
      this.$emit("task-deleted", index);
    },
    getTasks() {
      this.$emit("get-tasks");
    }
  }
};
</script>

<style scoped>
/* Стилі для компонента TaskList */
button.btn-warning {
  background-color: #ffc107;
  color: #333;
}

button.btn-warning:hover {
  background-color: #e0a800;
}

</style>
