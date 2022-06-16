<template>
  <tabs
    :disabledTabs="isEditing"
    :noneDisabledKey="noneDisabledKey"
    :tabs="tabComponents"
  >
    <template #title="Component">{{ Component.Title }}</template>
    <template #content="Component">
      <component
        :is="Component.ComponentName"
        @editingTab="editingTab(Component)"
      />
      <b-button @click="editingTab(Component)">
        {{ isEditing ? "Többi tab feloldása" : "Többi tab zárolása" }}
      </b-button>
    </template>
  </tabs>
</template>
<script>
import HelloWorld from "./HelloWorld.vue";
import Tabs from "./Tabs.vue";
export default {
  components: { HelloWorld, Tabs },
  name: "TabsByContent",
  data() {
    return {
      tabComponents: [
        {
          Key: "hello1",
          ComponentName: HelloWorld,
          Title: "Teszt HelloWorld Tab",
        },
        {
          Key: "hello2",
          ComponentName: HelloWorld,
          Title: "Teszt HelloWorld Tab 2",
        },
        {
          Key: "hello3",
          ComponentName: HelloWorld,
          Title: "Teszt HelloWorld Tab 2",
        },
      ],
      isEditing: false,
      noneDisabledKey: "isEditing",
    };
  },
  methods: {
    editingTab(editingComponent) {
      this.isEditing = !this.isEditing;
      const tab = this.tabComponents.find((t) => t.Key == editingComponent.Key);
      this.$set(tab, this.noneDisabledKey, this.isEditing);
    },
  },
};
</script>
