<template>
  <div class="insert-employee">
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
    <button @click="insertEmployeeApi">登録</button>
    <p v-show="isActive">{{ message }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "InsertEmployee",
  data() {
    return {
      id: "",
      name: "",
      pass: "pass",
      isActive: false,
      message: {},
    };
  },
  methods: {
    insertEmployeeApi() {
      const url = "http://localhost:8081/employee/";
      axios
        .post(url, {
          id: this.id,
          name: this.name,
          pass: this.pass,
        })
        .then((res) => {
          this.employee = res.data;
          this.message = "登録成功";
          this.isActive = true;
        })
        .catch((error) => {
          this.message = "登録失敗";
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
.insert-employee {
  display: inline-block;
  text-align: center;
}

.insert-employee div {
  text-align: left;
}

button {
  margin: 10px;
}
</style>
