<template>
  <div class="login">
    <Login />
  </div>
</template>

<script>
// @ is an alias to /src
import Login from "@/components/Login.vue";

export default {
  name: "LoginPage",
  components: {
    Login,
  },
};
</script>
