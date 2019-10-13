<template>
  <div class="v-accordion">
    <slot></slot>
  </div>
</template>

<script>
import vAccordionTab from "./vAccordionTab";

export default {
  props: {
    initialTabIndex: {
      type: Number,
      default: -1
    }
  },
  data() {
    return {
      activeTabIndex: -1
    };
  },
  computed: {
    tabs() {
      return this.$children;
    }
  },
  methods: {
    toggleTab(index) {
      this.activeTabIndex = index !== this.activeTabIndex ? index : -1;
      this.tabs.forEach((tab, i) =>
        tab.setVisibility(i === this.activeTabIndex)
      );
    },
    setTabIndexes() {
      this.tabs.forEach((tab, i) => (tab.index = i));
    },
    openTabByIndex(index) {
      this.tabs[index].setVisibility(true);
    },
    init() {
      this.setTabIndexes();
      this.initialTabIndex !== -1 && this.openTabByIndex(this.initialTabIndex);
      this.$on("tabToggled", this.toggleTab);
    }
  },
  mounted() {
    this.init();
  }
};
</script>

<style scoped>

</style>
