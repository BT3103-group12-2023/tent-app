<script>
import { RouterView } from "vue-router";
import ModalTutor from "./components/Modal-Tutor.vue";

export default {
    name: 'App',
    components: {
      ModalTutor,
    },
    data() {
      return {
        isModalVisible: false,
      };
    },
    methods: {
      showModal() {
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      }
    }
  };
</script>

<template>
  <header>
    <div>
      <HelloWorld msg="You did it!" />
      <h1>Test header</h1>
    </div>
  </header>

  <RouterView />

  <div id="app">
    <button
      type="button"
      class="btn"
      @click="showModal"
    >
      Open Modal!
    </button>

    <ModalTutor
      v-show="isModalVisible"
      @close="closeModal"
    />
  </div>
</template>

<style scoped></style>
