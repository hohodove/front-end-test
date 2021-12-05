<template>
  <div class="greet">
    <button @click="greet">Greet</button>
    <p>{{ greetdata.id }}</p>
    <p>{{ greetdata.content }}</p>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Greeting",
  data() {
    return {
      greetdata: {},
    };
  },
  methods: {
    greet() {
      axios
        .get("http://localhost:8081/greeting")
        .then((res) => {
          this.greetdata = res.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
