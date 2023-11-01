<template>
  <tr>
    <th scope="row">{{ task.id }}</th>
    <td>{{ task.text }}</td>
    <td>{{ task.status }}</td>
    <td>
      <button @click="deleteTask" class="btn btn-danger">Delete</button>
      <button @click="finishTask" class="btn btn-success ms-1">Finished</button>
    </td>
  </tr>
</template>

<script>
export default {
  props: {
    task: Object
  },
  methods: {
    deleteTask() {
      this.$emit("delete-task", this.task);
    },
    finishTask() {
      this.$emit("finish-task", this.task);
    }
  }
};
</script>

<style scoped>
/* Стилі для компонента TaskItem */
button.btn-danger {
  background-color: #dc3545;
  color: #fff;
  border: none;
  cursor: pointer;
  margin-left: 10px;
}

button.btn-success {
  background-color: #28a745;
  color: #fff;
  border: none;
  cursor: pointer;
  margin-left: 10px;
}

button:hover {
  background-color: #e0a800;
}
</style>
