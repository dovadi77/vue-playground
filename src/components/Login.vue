<template>
  <div class="container">
    <form @submit.prevent="validateData">
      <Input
        v-model="email"
        type="email"
        name="email"
        :errMsg="error.email"
        placeholder="name@example.com"
        label="Email Address"
      />
      <Input
        v-model="password"
        type="password"
        name="password"
        :errMsg="error.password"
        placeholder="Your Password"
        label="Password"
      />
      <button
        type="submit"
        class="btn btn-primary"
        :disabled="error.password.length > 0 || error.email.length > 0"
      >
        Login
      </button>
    </form>
  </div>
</template>

<script>
import Input from "./molecules/Input.vue";

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
      if (this.email.length === 0) {
        this.error.email = "Email tidak boleh kosong!";
      } else if (!this.validateEmail()) {
        this.error.email = "Format email tidak sesuai!";
      } else {
        this.error.email = "";
      }
    },
    password(val) {
      if (val.length === 0) {
        this.error.password = "Password tidak boleh kosong";
      } else {
        this.error.password = "";
      }
    },
  },
  components: {
    Input,
  },
};
</script>
