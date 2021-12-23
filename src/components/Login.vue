<template>
  <div class="login">
    <div>
      <label for="id">ID:</label>
      <input type="text" id="id" v-model="id" />
    </div>
    <div>
      <label for="name">NAME:</label>
      <input type="text" id="name" v-model="name" />
    </div>
    <div>
      <label for="pass">PASS:</label>
      <input type="text" id="pass" v-model="pass" />
    </div>
    <button @click="updateEmployeeApi">更新</button>
    <p v-show="isActive">{{ message }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      username: "",
      password: "",
      isActive: false,
      message: {},
    };
  },
  methods: {
    updateEmployeeApi() {
      const url = "http://localhost:8081/api/login";
      axios
        .put(
          url,
          {
            username: this.username,
            password: this.password,
          },
          {
            withCredentials: true,
          }
        )
        .then((res) => {
          this.employee = res.data;
          this.isActive = true;
        })
        .catch((error) => {
          this.message = "更新失敗";
          this.isActive = true;
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
input {
  margin: 3px;
  width: 50px;
  text-align: center;
}
.login {
  display: inline-block;
  text-align: center;
}

.login div {
  text-align: left;
}

button {
  margin: 10px;
}
</style>
