<template>
  <div class="search-employee">
    <SelectEmployee />
  </div>
</template>

<script>
// @ is an alias to /src
import SelectEmployee from "@/components/SelectEmployee.vue";

export default {
  name: "Home",
  components: {
    SelectEmployee,
  },
};
</script>
