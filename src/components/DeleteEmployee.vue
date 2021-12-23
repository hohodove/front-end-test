<template>
  <div class="delete-employee">
    <input type="text" v-model="id" />
    <button @click="deleteEmployeeApi">削除</button>
    <p v-show="isActive">{{ delete_number }}件削除</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DeleteEmployee",
  data() {
    return {
      id: "1",
      delete_number: {},
      isActive: false,
    };
  },
  methods: {
    deleteEmployeeApi() {
      const url = "http://localhost:8081/employee/" + this.id;
      axios
        .delete(url, { withCredentials: true })
        .then((res) => {
          this.delete_number = res.data;
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
.delete-employee {
  margin: 50px;
  text-align: center;
}

input {
  margin: 10px;
  width: 30px;
  text-align: center;
}
</style>
