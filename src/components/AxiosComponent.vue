<template>
  <!-- WORKFLOW : make an axios request, save it in the data object and then iterate/use it -->
  <div>
    <!-- Cookies -->
    <button @click="createCookie">create cookie</button>
    <button @click="deleteCookie">delete cookie</button>
    <!-- populate the response on the page -->
    <div v-for="user in users" :key="user.id">
      <h1>{{ user.first_name }} {{ user.last_name }}</h1>
      <h2>{{ user.email }}</h2>
      <!-- ------------------------------the + '\'s avatar' will display alt names for each images -->
      <img :src="user.avatar" :alt="user.first_name + '\'s avatar'" />
    </div>
  </div>
</template>

<script>
// 1.import axios
import axios from "axios";
import cookies from "vue-cookies";

export default {
  name: "AxiosComponent",
  //3. for each user returned, show them on the page with HTML
  // the resposne.data.data will print here
  data() {
    return {
      users: [],
    };
  },
  // 1.COOKIE EXAMPLE
  methods: {
    // set cookies
    createCookie() {
      cookies.set(`testCookie`, `This is a test`);
    },
    deleteCookies() {
      cookies.remove(`deletCookie`);
    },
    // get cookies
    getCookie() {
      let value = cookies.get(`testCookie`);
      console.log(value);
    },
  },
  //2.
  mounted() {
    axios
      .request({
        url: "https://reqres.in/api/users",
        method: "GET",
      })
      //the arrow function is a new way to write the function.
      .then((response) => {
        this.users = response.data.data;
      })
      .catch((error) => {
        console.log(error);
      });
  },
};
</script>

<style scoped>
</style>
