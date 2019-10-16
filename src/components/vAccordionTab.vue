<template>
  <div @click="toggleTab" class="accordion-tab" :class="{horizontal: horizontal}">
    <div class="tab-head">Tab {{index + 1}}</div>
    <div class="tab-body" v-show="opened">
      <slot></slot>
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
.accordion-tab {
  display: flex;
  flex-direction: column;
  margin-bottom: 2px;
}

.accordion-tab.horizontal {
  flex-direction: row;
}

.tab-head {
  padding: 2%;
  font: 20px Arial;
  color: #555;

  background: #41b883;
}

.accordion-tab.active {
  opacity: 1;
}

.tab-body {
  min-height: 30px;

  background: #eee;
}
</style>