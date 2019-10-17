<template>
  <div @click="toggleTab" class="v-accordion-tab"
       :class="{horizontal: horizontal, vertical: !horizontal, active: opened}">
    <div class="tab-head">
      <slot name="tab-head">
        <p class="tab-title">v-accordion-tab</p>
      </slot>
    </div>
    <div class="tab-body">
      <slot name="tab-body">
      </slot>
    </div>
  </div>
</template>


<script>
    export default {
        data() {
            return {
                opened: false,
                horizontal: false,
                index: 0
            };
        },
        methods: {
            setVisibility(visible) {
                this.opened = visible;
            },
            toggleTab() {
                this.$parent.$emit("tabToggled", this.index);
            }
        }
    };
</script>

<style scoped>

  .v-accordion-tab {
    display: flex;
    flex-flow: column nowrap;
  }


  .horizontal .v-accordion-tab {
    display: flex;
    flex-flow: row nowrap;
    align-items: stretch;;
    height: auto;
  }

  .v-accordion-tab {
    transition: height ease-in 0.3s;
    height: 52px;
  }

  .v-accordion-tab.active {
    height: 250px;
  }

  .horizontal .v-accordion-tab {
    transition: width ease-in 0.3s;
    width: 58px;
    height: auto;
  }

  .horizontal .v-accordion-tab.active {
    width: 500px;
  }

  .horizontal .v-accordion-tab .tab-body > div {
    height: 100%;
    transition-duration: 0.1s;
    opacity: 0;
  }

  .horizontal .v-accordion-tab.active .tab-body > div {
    opacity: 1;
    transition: opacity 0.4s linear 0.4s;
  }

  .tab-head {
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
    background: #29b6f6;
    box-shadow: 2px 0px 2px #e9eaeb;
    cursor: pointer;
  }

  .tab-head > div {
    display: flex;
    flex-flow: row nowrap;
  }

  .horizontal .tab-head {
    width: 52px;
    min-width: 52px;
    height: auto;
  }

  .tab-head {
    justify-content: center;
    width: 100%;
    height: 46px;
    min-height: 46px;
    background: #35495e;
  }

  .active .tab-head {
    background: #41b883;
  }

  .tab-head .tab-title {
    display: flex;
    white-space: nowrap;
    color: #fff;
    font: 18px Arial;
  }

  .horizontal .tab-title {
    transform: rotate(270deg);
  }

  .tab-body {
    height: 300px;
    margin: 6px 0;

    overflow: hidden;
    background: #f3acac;
  }

  .horizontal .tab-body {
    width: 500px;
    margin: 0 6px;
  }

</style>
