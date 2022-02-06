<template>
  <div class="container">
    <Header msg="Welcome to Vue.js App with Bootstrap 5" />
    <div class="my-3">
      <Login @accountValid="checkAccount" v-if="!loggedIn" />
      <Dashboard v-if="loggedIn" msg="yeay berhasil!" :tasks="tasks" />
    </div>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Login from "@/components/Login.vue";
import Dashboard from "@/components/Dashboard.vue";
import tasks from "@/data/todo.json";

export default {
  name: "App",
  data() {
    return { loggedIn: false, tasks: tasks };
  },
  components: {
    Header,
    Login,
    Dashboard,
  },
  methods: {
    checkAccount(val) {
      this.loggedIn = val;
    },
  },
};
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
