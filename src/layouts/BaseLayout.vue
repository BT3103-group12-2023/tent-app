<script setup>
import { useRouter } from "vue-router";
import { logOut } from "../lib/handlers/auth";

const router = useRouter();

const logOutOnClick = async () => {
  await logOut();
  router.push("/auth");
};
</script>

<template>
  <nav>
    <h1>Tent</h1>
    <div id="navbar-buttons">
      <router-link to="/student-listings">Look for students</router-link>
      <router-link to="/tutor-listings">Look for tutors</router-link>
      <router-link to="/me">Settings</router-link>
      <p @click="logOutOnClick">Log out</p>
    </div>
  </nav>

  <!-- <slot /> -->
  <router-view />
</template>

<style scoped>
nav {
  background-color: var(--tent-orange);
  color: white;
  padding: 1rem 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

#navbar-buttons {
  justify-self: end;
  display: flex;
  gap: 1rem;
}

#navbar-buttons a,
#navbar-buttons p {
  color: white;
  text-decoration: none;
  border: none;
  background-color: inherit;
  cursor: pointer;
}

#navbar-buttons a:hover,
#navbar-buttons p:hover {
  text-decoration: underline white 2px;
  font-style: italic;
}
</style>
