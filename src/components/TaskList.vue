<template>
  <div class="container-fluid add-task">
    <div class="container p-1 bg-white shadow-lg rounded col-sm-12 col-md-5">
      <input
        type="text"
        class="form-control border-0"
        placeholder="Add Todo!"
        v-model="newTodo"
        @keyup.enter="addTodo"
      />
    </div>

    <div
      class="container mt-5 mb-5 pt-3 bg-white shadow-lg rounded col-sm-12 col-md-5"
    >
      <div v-for="(task, index) in tasks" :key="task.id">
        <div class="row mt-1 mb-1">
          <div class="col">
            <div class="form-group">
              <div class="row">
                <div class="col ml-3 form-check">
                  <input type="checkbox" class="form-check-input" />
                  <div
                    v-if="!task.editing"
                    @dblclick="editTodo(task)"
                    class="title-task col"
                  >
                    {{ task.title }}
                  </div>
                  <input
                    v-else
                    type="text"
                    class="form-control"
                    name=""
                    id=""
                    v-model="task.title"
                    @blur="doneEdit(task)"
                    @keyup.enter="doneEdit(task)"
                    @keyup.esc="cancelEdit(task)"
                  />
                </div>
              </div>
            </div>
          </div>
          <div class="col-sm-1 col-md-1">
            <div class="text-right mr-2">
              <i class="fa fa-times remove-todo" @click="removeTodo(index)"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  data() {
    return {
      newTodo: "",
      idForTodo: 3,
      tasks: []
    };
  },

  methods: {
    addTodo() {
      if (this.newTodo.trim() == 0) {
        return;
      }
      this.tasks.push({
        id: this.idForTodo,
        title: this.newTodo,
        completed: false,
        editing: false
      });
      this.newTodo = "";
      this.idForTodo++;
    },
    removeTodo(index) {
      this.tasks.splice(index, 1);
    },
    editTodo(task) {
      task.editing = true;
      task.beforeEditCache = todo.title;
    },
    doneEdit(task) {
      task.editing = false;
    },
    cancelEdit(task) {
      task.title = this.beforeEditCache;
      task.editing = false;
    }
  }
};
</script>

<style>
textarea:focus,
textarea.form-control:focus,
input.form-control:focus,
input[type="text"]:focus,
input[type="password"]:focus,
input[type="email"]:focus,
input[type="number"]:focus,
[type="text"].form-control:focus,
[type="password"].form-control:focus,
[type="email"].form-control:focus,
[type="tel"].form-control:focus,
[contenteditable].form-control:focus {
  box-shadow: inset 0 -1px 0 #ddd;
}
.remove-todo:hover {
  cursor: pointer;
  color: #ef5350;
}
.title-task {
  cursor: default;
}
</style>
