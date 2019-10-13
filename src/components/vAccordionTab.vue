<template>
  <div @click="toggleTab" class="accordion-tab" >
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
  margin-bottom: 2px;
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