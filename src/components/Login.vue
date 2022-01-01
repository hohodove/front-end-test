<template>
  <div class="login">
    <div>
      <label for="name">USERNAME:</label>
      <input type="text" id="username" v-model="username" />
    </div>
    <div>
      <label for="pass">PASSWORD:</label>
      <input type="text" id="password" v-model="password" />
    </div>
    <button @click="loginRequest">ログイン</button>
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
    loginRequest() {
      const url = "http://localhost:8081/login";
      const param = new FormData();
      param.append("username", this.username);
      param.append("password", this.password);
      axios
        .post(url, param, { withCredentials: true })
        .then((res) => {
          this.message = "ログイン成功";
          this.employee = res.data;
          this.isActive = true;
        })
        .catch((error) => {
          this.message = "ログイン失敗";
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
  width: 70px;
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
