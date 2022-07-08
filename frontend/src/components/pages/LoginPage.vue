<template>
  <div class="auth">
    <div class="container container--flex">
      <div class="card auth__login">
        <form id="login-form" @submit.prevent="handleSubmit">
          <InputBase
            v-model="loginData.email"
            label="E-mail"
            name="login-email"
            type="email"
          />
          <!-- <InputBase /> -->
          <button class="btn btn__primary" type="submit">Login</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from "vue";
import InputBase from "@/components/UI/InputBase";

interface LoginData {
  email: string;
  password: string;
}

const loginData: LoginData = reactive({
  email: "",
  password: "",
});

const handleSubmit = () => {
  console.log(loginData);
};
</script>
