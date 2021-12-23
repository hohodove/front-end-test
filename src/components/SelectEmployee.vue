<template>
  <div class="select-employee">
    <input type="text" v-model="id" />
    <button @click="selectEmployeeApi">検索</button>
    <p v-show="isActive">{{ employee.id }}, {{ employee.name }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SelectEmployee",
  data() {
    return {
      id: "1",
      employee: {},
      isActive: false,
    };
  },
  methods: {
    selectEmployeeApi() {
      const url = "http://localhost:8081/employee/" + this.id;
      axios
        .get(url, { withCredentials: true })
        .then((res) => {
          this.employee = res.data;
          this.isActive = true;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
.select-employee {
  margin: 0 0 50px;
  text-align: center;
}

input {
  margin: 10px;
  width: 30px;
  text-align: center;
}
</style>
