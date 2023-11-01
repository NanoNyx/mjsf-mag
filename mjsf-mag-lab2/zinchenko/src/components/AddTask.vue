<template>
  <div>
    <form class="row row-cols-lg-auto g-3 align-items-center">
      <div class="col-12">
        <div class="form-outline">
          <input v-model="newTask" class="form-control" placeholder="Enter a new task" />
          <label class="form-label">Enter a task here</label>
        </div>
      </div>
      <div class="col-12">
        <button @click="addTask" class="btn btn-primary">Save</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: ""
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.$emit("task-added", this.newTask);
        this.newTask = "";
      }
    }
  }
};
</script>

<style scoped>
/* Стилі для компонента AddTask */
button.btn-primary {
  background-color: #007bff;
  color: #fff;
}

button.btn-primary:hover {
  background-color: #0056b3;
}
</style>
