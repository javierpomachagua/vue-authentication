<template>
  <div id="dashboard">
    <h1>That's the dashboard!</h1>
    <p>You should only get here if you're authenticated!</p>
    <p v-if="email">Your email address: {{ email }}</p>
  </div>
</template>

<script>
import Vuex from 'vuex';
import axios from "axios";

export default {
  computed: {
    email() {
      return this.$store.getters.user ? this.$store.getters.user.email : false;
    }
  },
  created() {
    this.$store.dispatch('fetchUser');
  }
};
</script>

<style scoped>
h1,
p {
  text-align: center;
}

p {
  color: red;
}
</style>