<template>
  <div class="container">
    <div class="mb-3">
      <label for="email" class="form-label">Email address</label>
      <input
        type="email"
        class="form-control"
        id="email"
        placeholder="name@example.com"
        v-model="email"
      />
      <small class="text-danger" v-if="error.email.length > 0">{{
        error.email
      }}</small>
    </div>
    <div class="mb-3">
      <label for="password" class="form-label">Password</label>
      <input
        type="password"
        class="form-control"
        id="password"
        placeholder="Your password"
        v-model="password"
      />
      <small class="text-danger" v-if="error.password.length > 0">{{
        error.password
      }}</small>
    </div>
  </div>
  <button
    type="button"
    class="btn btn-primary"
    @click="validateData"
    :disabled="error.password.length > 0 && error.email.length > 0"
  >
    Login
  </button>
</template>

<script>
export default {
  name: "Login",
  emits: ["accountValid"],
  data() {
    return {
      error: {
        email: "",
        password: "",
      },
      email: "",
      password: "",
    };
  },
  methods: {
    validateEmail() {
      const re =
        /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(this.email);
    },
    validatePassword() {
      return this.password.length > 8;
    },
    validateData() {
      if (this.error.password.length === 0 && this.error.email.length === 0) {
        this.$emit("accountValid", true);
      }
    },
  },
  watch: {
    email() {
      if (!this.validateEmail()) {
        this.error.email = "Format email tidak sesuai!";
      } else {
        this.error.email = "";
      }
    },
    password(val) {
      if (val.length < 8) {
        this.error.password = "Password minimal 8 karakter";
      } else {
        this.error.password = "";
      }
    },
  },
};
</script>
