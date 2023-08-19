<template>
  <v-app>
    <v-container>
      <Header></Header>
    </v-container>
    <Container style="margin-top:50px"/>
</v-app>
</template>

<script>
import Container from "./components/Container.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Container,
    Header
  }
};
</script>

