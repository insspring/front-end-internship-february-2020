<template>
  <div class="home">
    <Header></Header>
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import Header from "../components/Header";

export default {
  name: "home",
  components: {
      Header,
      HelloWorld,
  }
};
</script>
