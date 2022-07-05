<template>
  <div id="app">
    <!-- EXERCISE 04: Two-way data binding -->
    <h1>Ex 04: Two-way Data binding</h1>
    Available users:
    <li v-for="user in users">{{ user.name }}</li>
    <br />
    Search a user age: <input v-model="userToSearch" />
    <!-- Instruction 1 answer -->
    <p>
      User entered <strong>{{ userToSearch }}</strong>
    </p>
    <br />
    <Child @fetchUsers="fetchUsersService" :userToSearch="userToSearch" />
    <!--Instruction 2 answer -->
  </div>
</template>

<script>
import Child from './Child.vue';

export default {
  name: 'App',
  data: () => ({
    userToSearch: '', // Instruction 1 answer
    users: [
      { name: 'Mario', age: 29 },
      { name: 'David', age: 40 },
      { name: 'John', age: 39 },
    ],
  }),
  components: {
    Child,
  },
  methods: {
    async fetchUsersService(callback) {
      const response = await this.fakeCall();
      callback(this.users);
    },
    fakeCall() {
      return new Promise((resolve) => {
        setTimeout(function () {
          resolve();
        }, 2000);
      });
    },
  },
};
</script>

<style></style>
