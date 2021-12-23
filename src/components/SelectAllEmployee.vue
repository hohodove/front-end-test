<template>
  <div class="select-all-employees">
    <ul class="ul-center">
      <li v-for="employee in employees" :key="employee.id">
        {{ employee.id }}, {{ employee.name }}
      </li>
    </ul>
    <br />
    <button @click="refreshEmployees">最新化</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "SelectAllEmployee",
  data() {
    return {
      employees: {},
    };
  },
  created: function () {
    this.refreshEmployees();
  },
  methods: {
    refreshEmployees: function () {
      const url = "http://localhost:8081/employee/";
      axios
        .get(url, { withCredentials: true })
        .then((res) => {
          this.employees = res.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>

<style scoped>
.select-all-employees {
  margin: 0 0 50px;
  text-align: center;
}
.ul-center {
  text-align: left;
  display: inline-block;
}
</style>
