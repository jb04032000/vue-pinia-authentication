<script setup>
import { ref } from "vue-demi";
import { useAuthStore } from "../stores/auth.store";

let username = ref("");
let password = ref("");

function onSubmit(values) {
  console.log(values);
  const authStore = useAuthStore();
  const { username, password } = values;

  return authStore
    .login(username, password)
    .catch((error) => console.log(error));
}
</script>

<template>
  <div>
    <div class="alert alert-info">
      Username: test<br />
      Password: test
    </div>
    <h2>Login</h2>
    <form @submit.prevent="onSubmit">
      <div class="form-group">
        <label>Username</label>
        <input
          name="username"
          type="text"
          class="form-control"
          v-model="username"
        />
      </div>
      <div class="form-group">
        <label>Password</label>
        <input
          name="password"
          type="password"
          class="form-control"
          v-model="password"
        />
      </div>
      <div class="form-group">
        <button class="btn btn-primary">Login</button>
      </div>
    </form>
  </div>
</template>
