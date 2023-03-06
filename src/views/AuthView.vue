<script setup>
import { storeToRefs } from "pinia";
import { ref, watchEffect } from "vue";
import useAuthStore from "../stores/authStore";
import { logOut, signIn, signUp } from "../lib/handlers/auth";

const { user } = storeToRefs(useAuthStore());

const mode = ref("sign-in");

const inputs = ref({
  email: "",
  password: "",
  phoneNumber: "",
  telegramHandle: "",
});

/**
 * Changes mode of the current form
 * @param {("sign-in"|"sign-up")} newMode
 */
const changeModeOnClick = (newMode) => {
  mode.value = newMode;
};

watchEffect(() => {
  console.log("current user", user.value);
});
</script>

<template>
  <div id="form-box">
    <div id="mode-buttons">
      <button @click="changeModeOnClick('sign-in')">Sign In</button>
      <button @click="changeModeOnClick('sign-up')">Sign Up</button>
      <button @click="logOut">Log Out</button>
    </div>

    <div id="form-inputs" v-if="mode === 'sign-in'">
      <h1>Sign In</h1>
      <form @submit="signIn(inputs.email, inputs.password)">
        <label>Email</label>
        <input type="text" v-model="inputs.email" />
        <label>Password</label>
        <input type="text" v-model="inputs.password" />
        <button type="submit">Sign In</button>
      </form>
    </div>

    <div id="form-inputs" v-else-if="mode === 'sign-up'">
      <h1>Sign Up</h1>
      <form
        @submit="signUp(inputs.email, inputs.password, inputs.phoneNumber, inputs.telegramHandle)"
      >
        <label>Email</label>
        <input type="text" v-model="inputs.email" />
        <label>Password</label>
        <input type="text" v-model="inputs.password" />
        <label>Phone No.</label>
        <input type="text" v-model="inputs.phoneNumber" />
        <label>Telegram</label>
        <input type="text" v-model="inputs.telegramHandle" />

        <button type="submit">Sign Up</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
#form-box {
  position: relative;
  top: 30%;
  margin: auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 30%;
  gap: 1rem;
  padding: 2rem;
  padding-top: 4rem;
  border: 3px solid gray;
  border-radius: 1rem;
}

#mode-buttons {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 1rem;
}

#form-inputs {
  width: 100%;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

#form-inputs h1 {
  text-align: center;
}

form {
  display: grid;
  grid-template-columns: 30% auto;
  gap: 0.25rem 0.5rem;
}

form button {
  grid-column: span 2;
  border: none;
  background-color: gray;
  padding: 0.5rem;
  font-size: 1.2rem;
  color: white;
  border-radius: 0.5rem;
  margin-top: 2rem;
  cursor: pointer;
}

form button:hover {
  background-color: green;
  transition: background-color 300ms;
  transition-timing-function: ease-in-out;
}
</style>
