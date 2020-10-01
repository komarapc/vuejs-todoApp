<template>
  <div id="app">
    <div class="jumbotron jumbotron-fluid">
      <div class="container text-white">
        <h1 class="display-4">VueJS Todo App</h1>
        <p class="lead">
          komar.izmi@gmail.com
        </p>
      </div>
    </div>
    <TaskList></TaskList>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import TaskList from "./components/TaskList";
export default {
  name: "App",
  components: {
    HelloWorld,
    TaskList
  }
};
</script>

<style>
.jumbotron {
  height: 450px;
  background-color: #009688;
}
.container-fluid.add-task {
  margin-top: -200px;
}
</style>
