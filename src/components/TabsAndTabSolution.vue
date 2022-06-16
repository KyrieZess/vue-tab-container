<template>
  <div>
    Aktív tab sorszáma: {{ activeTabNumber }}<br />
    Új tab index: {{ newTabIndex }}, Előző tab index: {{ prevTabIndex }}
    <tabs @activateTab="activateTab">
      <tab @click="activeTabNumber = 1" title="Teszt HelloWorld Tab">
        <hello-world />
      </tab>
      <tab @click="activeTabNumber = 2">
        <template #title> Teszt HelloWorld Tab 2 </template>
        <hello-world />
      </tab>
      <tab @click="activeTabNumber = 3">
        <template #title> Teszt HelloWorld Tab 3 </template>
        <hello-world />
      </tab>
    </tabs>
  </div>
</template>
<script>
import HelloWorld from "./HelloWorld.vue";
import Tab from "./Tab.vue";
import Tabs from "./Tabs.vue";
export default {
  components: { Tabs, Tab, HelloWorld },
  name: "TabsAndTabSolution",
  data() {
    return {
      activeTabNumber: 1,
      newTabIndex: 0,
      prevTabIndex: 0,
    };
  },
  methods: {
    activateTab(activateObj) {
      this.newTabIndex = activateObj.NewTabIndex;
      this.prevTabIndex = activateObj.PrevTabIndex;
    },
  },
};
</script>
