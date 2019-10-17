<template>
  <div class="v-accordion" :class="{horizontal: horizontal, vertical: !horizontal}">
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
            setInitialIndex() {
                this.initialTabIndex !== -1 && this.openTabByIndex(this.initialTabIndex);
            },
            openTabByIndex(index) {
                this.tabs[index].setVisibility(true);
            },
            init() {
                this.setTabIndex();
                this.setInitialIndex();
                this.$on("tabToggled", this.toggleTab);
            }
        },
        watch: {
            tabsOrientation() {
                this.tabs.forEach(tab => (tab.horizontal = this.horizontal));
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
    box-sizing: border-box;
    flex-flow: column nowrap;
    width: 400px;
  }

  .v-accordion.horizontal {
    flex-flow: row nowrap;
    height: 300px;
    width: 700px;
  }
</style>
