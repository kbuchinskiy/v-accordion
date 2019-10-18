<template>
  <div class="v-accordion" :class="{horizontal: horizontal, vertical: !horizontal}">
    <slot></slot>
  </div>
</template>

<script>
    export default {
        props: {
            tabToOpenInitially: {
                type: Number,
                default: -1
            },
            oneTabToOpen: {
                type: Boolean,
                default: true
            },
            horizontal: {
                type: Boolean,
                default: false
            },
        },
        data() {
            return {
                activeTabs: []
            };
        },
        computed: {
            tabs() {
                return this.$children;
            },
        },
        watch: {
            tabsOrientation() {
                this.tabs.forEach(tab => tab.horizontal = this.horizontal);
            },
            activeTabs() {
                this.tabs.forEach(tab => tab.setVisibility(this.activeTabs.includes(tab.index)));
            },
        },
        methods: {
            setTabIndex() {
                this.tabs.forEach((tab, i) => (tab.index = i));
            },
            setInitialTabs() {
                if (this.tabToOpenInitially !== -1) {
                    this.activeTabs.push(this.tabToOpenInitially);
                }
            },
            toggleTabHandler(tab) {
                if (this.activeTabs.includes(tab)) {
                    this.activeTabs.splice(this.activeTabs.indexOf(tab), 1);
                } else {
                    if (this.oneTabToOpen) {
                        this.activeTabs = []
                    }
                    this.activeTabs.push(tab)
                }
            },
            init() {
                this.setTabIndex();
                this.setInitialTabs();
                this.$on("tabToggled", this.toggleTabHandler);
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
