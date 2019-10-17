<template>
  <div id="app">

    <button @click="isAccordionHorizontal = !isAccordionHorizontal" class="toggle-btn">
      <span v-show="!isAccordionHorizontal">Horizontal</span>
      <span v-show="isAccordionHorizontal">Vertical</span>
    </button>

    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <v-accordion :initial-tab-index="1" :horizontal="isAccordionHorizontal">
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos
        voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus
        reiciendis repellat dolorum possimus.
      </v-accordion-tab>
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos
        voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus
        reiciendis repellat dolorum possimus.
      </v-accordion-tab>
      <v-accordion-tab>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Totam impedit dicta neque quos
        voluptatibus nemo, blanditiis accusantium placeat, error voluptates iure ipsam aspernatur atque sed delectus
        reiciendis repellat dolorum possimus.
      </v-accordion-tab>
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
        },
        data() {
            return {
                isAccordionHorizontal: false
            }
        }
    };
</script>

<style>
  body {
    margin: 0;
  }

  #app {
    font-family: "Avenir", Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    display: flex;
    flex-flow: column;
    align-items: center;
    justify-content: center;

    height: 100vh;
  }

  .toggle-btn {

    position: fixed;
    top: 20vh;

    border: none;
    background: #41b883;
    padding: 1%;
    color: #fff;
  }

</style>
