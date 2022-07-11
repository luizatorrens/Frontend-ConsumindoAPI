<script setup>
import HeaderComp from "./components/template/HeaderComp.vue";
import RodapeComp from "./components/template/RodapeComp.vue";
</script>
<template>
  <HeaderComp />
  <main>
    <RouterView />
  </main>
  <RodapeComp />
</template>

<style>
@import "@/assets/base.css";
@import "@/assets/style.css";

#app {
  max-width: 1280px;
  margin: 0 auto;
  /*padding: 2rem;*/
  height: 100vh;

  font-weight: normal;
}
header {
  background-color: lightskyblue;
  color: white;
  height: 15%;
  font-size: 1.3rem;
  display: flex;
}
footer {
  background-color: lightskyblue;
  color: rgb(29, 29, 173);
  height: 5%;
  font-size: 1.3rem;
}
main {
  height: 80%;
  background-color: white;
  color: black;
}
a {
  text-decoration: none;
  color: inherit;
}
</style>
