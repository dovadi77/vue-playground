<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <HelloWorld msg="Welcome to Your Vue.js App with Bootstrap 5" />
  <Login @accountValid="checkAccount" v-if="!loggedIn" />
  <LoggedIn v-if="loggedIn" msg="yeay berhasil!" />
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Login from "./components/Login.vue";
import LoggedIn from "./components/LoggedIn.vue";

export default {
  name: "App",
  data() {
    return { loggedIn: false };
  },
  components: {
    HelloWorld,
    Login,
    LoggedIn,
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
