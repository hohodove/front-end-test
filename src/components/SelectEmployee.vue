<template>
  <div class="select-employee">
    <input type="text" v-model="id" /><br />
    <button @click="selectApi">従業員検索</button>
    <p>{{ employee.id }}, {{ employee.name }}</p>
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
    };
  },
  methods: {
    selectApi() {
      const url = "http://localhost:8081/employee/" + this.id;
      axios
        .get(url)
        .then((res) => {
          this.employee = res.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
