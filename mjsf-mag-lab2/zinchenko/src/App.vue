<template>
  <div>
    <section class="vh-100" style="background-color: #eee;">
      <div class="container py-5 h-100">
        <div class="row d-flex justify-content-center align-items-center h-100">
          <div class="col col-lg-9 col-xl-7">
            <div class="card rounded-3">
              <div class="card-body p-4">
                <h4 class="text-center my-3 pb-3">To Do App</h4>
                
                <add-task @task-added="addTask" />
                <task-list :tasks="tasks" @task-deleted="deleteTask" @finish-task="finishTask" />
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import AddTask from './components/AddTask.vue';
import TaskList from './components/TaskList.vue';

export default {
  components: {
    'add-task': AddTask,
    'task-list': TaskList,
  },
  data() {
    return {
      tasks: [
        { id: 1, text: 'Buy groceries for next week', status: 'In progress' },
        { id: 2, text: 'Renew car insurance', status: 'In progress' },
        { id: 3, text: 'Sign up for an online course', status: 'In progress' },
      ],
    };
  },
  methods: {
    addTask(newTaskText) {
      const newTask = {
        id: this.tasks.length + 1,
        text: newTaskText,
        status: 'In progress',
      };
      this.tasks.push(newTask);
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    },
    finishTask(index) {
      this.tasks[index].status = 'Finished';
    },
  },
};
</script>

<style>
/* Додані стилі для App.vue */
body, html {
  height: 100%;
  margin: 0;
}

.card {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  background-color: #000000;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
}

.btn-primary:hover {
  background-color: #0056b3;
}
</style>
