<template>
  <div class="v-accordion" :class="{horizontal: horizontal}">
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    initialTabIndex: {
      type: Number,
      default: -1
    },
    horizontal: {
      type: Boolean,
      default: false
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
    setTabIndex() {
      this.tabs.forEach((tab, i) => (tab.index = i));
    },
    setTabOrientation() {
      this.tabs.forEach(tab => (tab.horizontal = this.horizontal));
    },
    setInitialIndex() {
      this.initialTabIndex !== -1 && this.openTabByIndex(this.initialTabIndex);
    },
    openTabByIndex(index) {
      this.tabs[index].setVisibility(true);
    },
    init() {
      this.setTabIndex();
      this.setTabOrientation();
      this.setInitialIndex();
      this.$on("tabToggled", this.toggleTab);
    }
  },
  mounted() {
    this.init();
  }
};
</script>

<style scoped>
.v-accordion {
  display: flex;
  flex-direction: column;
}

.v-accordion.horizontal  {
  flex-direction: row;
}
</style>
