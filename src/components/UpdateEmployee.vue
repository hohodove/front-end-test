<template>
  <div class="update-employee">
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
  name: "UpdateEmployee",
  data() {
    return {
      id: "1",
      name: "",
      pass: "",
      isActive: false,
      message: {},
    };
  },
  methods: {
    updateEmployeeApi() {
      const url = "http://localhost:8081/employee/" + this.id;
      axios
        .put(url, {
          id: this.id,
          name: this.name,
          pass: this.pass,
        })
        .then((res) => {
          this.employee = res.data;
          this.message = "更新成功";
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
.update-employee {
  display: inline-block;
  text-align: center;
}

.update-employee div {
  text-align: left;
}

button {
  margin: 10px;
}
</style>
