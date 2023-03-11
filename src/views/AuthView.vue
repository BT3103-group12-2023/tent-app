<script setup>
import { ref } from "vue";
import { signIn, signUp } from "../lib/handlers/auth";

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
</script>

<template>
  <div id="background-image">
    <div id="left-section">
      <h1 id="tent-title">Tent</h1>

      <div id="mode-buttons">
        <button @click="changeModeOnClick('sign-in')">Sign In</button>
        <button @click="changeModeOnClick('sign-up')">Sign Up</button>
      </div>

      <form @submit="signIn(inputs.email, inputs.password)" v-show="mode === 'sign-in'">
        <label>Email</label>
        <input type="text" v-model="inputs.email" />

        <label>Password</label>
        <input type="text" v-model="inputs.password" />

        <button type="submit">Sign In</button>
      </form>

      <form
        @submit="signUp(inputs.email, inputs.password, inputs.phoneNumber, inputs.telegramHandle)"
        v-show="mode === 'sign-up'"
      >
        <label>Email</label>
        <input type="text" v-model="inputs.email" />

        <label>Password</label>
        <input type="text" v-model="inputs.password" />

        <label>Phone Number</label>
        <input type="text" v-model="inputs.phoneNumber" />

        <label>Telegram Handle</label>
        <input type="text" v-model="inputs.telegramHandle" />

        <button type="submit">Sign Up</button>
      </form>
    </div>
  </div>
</template>

<style scoped>
#background-image {
  width: 100%;
  height: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.65), rgba(0, 0, 0, 0.65)),
    url("../assets/tuitionimage.jpg");
  background-size: 100%;
  background-repeat: no-repeat;
}

#left-section {
  width: 20%;
  height: 100%;
  background: rgba(0, 0, 0, 0.2);
  color: white;

  padding: 5rem;
  box-sizing: border-box;
}

#tent-title {
  font-size: 5rem;
  margin-bottom: 0.5rem;
}

#mode-buttons {
  display: flex;
  gap: 1rem;
  margin-bottom: 5rem;
}

#mode-buttons button {
  background-color: inherit;
  border: none;
  color: white;
  font-size: 2rem;
  cursor: pointer;
}

#mode-buttons button:hover {
  color: gray;
  transition: color 150ms;
}

form {
  display: flex;
  flex-direction: column;
}

form label {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
}

form input {
  font-size: 1.5rem;
  padding: 0.5rem;
  margin-bottom: 2rem;
  border-radius: 1rem;
}

form button {
  background: rgb(255, 144, 66);
  color: white;
  border: none;
  font-size: 1.5rem;
  padding: 0.5rem;
  margin-bottom: 3rem;
  border-radius: 1rem;
  cursor: pointer;
}

form button:hover {
  background: rgba(255, 144, 66, 0.8);
  transition: background 150ms;
}
</style>
