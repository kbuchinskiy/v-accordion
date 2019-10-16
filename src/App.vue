<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <v-accordion :initial-tab-index="1" :horizontal="true">
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus reiciendis repellat dolorum possimus.</v-accordion-tab>
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus reiciendis repellat dolorum possimus.</v-accordion-tab>
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus reiciendis repellat dolorum possimus.</v-accordion-tab>
    </v-accordion>
  </div>
</template>

<script>
import vAccordion from "./components/vAccordion.vue";
import vAccordionTab from "./components/vAccordionTab";

export default {
  components: {
    vAccordion,
    vAccordionTab
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.accordion-tab .tab-body {
  min-height: 100px;
  padding: 3%;
  font-size: 20px;
  text-align: justify;
}
</style>
