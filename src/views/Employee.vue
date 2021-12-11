<template>
  <div class="search-employee">
    <SelectAllEmployee />
    <SelectEmployee />
    <InsertEmployee />
    <DeleteEmployee />
    <UpdateEmployee />
  </div>
</template>

<script>
// @ is an alias to /src
import SelectEmployee from "@/components/SelectEmployee.vue";
import SelectAllEmployee from "../components/SelectAllEmployee.vue";
import InsertEmployee from "../components/InsertEmployee.vue";
import DeleteEmployee from "../components/DeleteEmployee.vue";
import UpdateEmployee from "../components/UpdateEmployee.vue";

export default {
  name: "Home",
  components: {
    SelectEmployee,
    SelectAllEmployee,
    InsertEmployee,
    DeleteEmployee,
    UpdateEmployee,
  },
};
</script>
